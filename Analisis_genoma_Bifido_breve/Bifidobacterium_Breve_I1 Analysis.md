---
autores: Roberto Luarte
organismos: Bifidobacterium_Breve_I1
tecnologia-seq:
---
# Pipeline
En este reporte se utilizaron las siguientes herramientas:
* FASTQC
* Trimmomatic 
* SPADES
* PROKKA
* QUAST
* GtoTree
* BLAST KOALA
* DBcan

# Reads

## Quality Control
# Trimming
## Quality Control
# Assembly
## Quality Control
Para realizar el control de calidad se utilizó el programa QUAST, para esto se generaron scripts para descargar todos los assemblies disponibles en NCBI de Bifidobacterium_Breve 
#### Codigo

```bash

#Vamos a crear un script para descargar genomas correspondientes a pediococcus y biff  
idobacteria;  
#Primero creamos una variable para asignar el enlace al servidor ftp de NCBI  
  
genbank=ftp://ftp.ncbi.nlm.nih.gov/genomes/genbank/bacteria/  
#Luego creamos una variable para el Taxa que tenemos como blanco  
targetTaxa=Bifidobacterium_breve  
#Creamos el directorio de output  
outDir=BifidoGenomes  
mkdir -p $outDir  
#Este comando seria para descargar los genomas que existen para nuestro target taxa  
genomes=`curl -ls ftp://ftp.ncbi.nlm.nih.gov/genomes/genbank/bacteria/$targetTaxa/lat  
est_assembly_versions/`  
  
#Ahora generamos el loop para descargarlos todos  
  
for g in $genomes  
do    
       mkdir $outDir/$g  
  
       wget ftp://ftp.ncbi.nlm.nih.gov/genomes/genbank/bacteria/$targetTaxa/latest_a  
ssembly_versions/$g/* -P $outDir/$g  
done
```
Para extraer los assemblies, que son los archivos que nos interesan en particular, se utilizó la línea de comando para tener todos los assemblies en un mismo directorio
```bash
find /ruta/del/directorio -type f -name "*.fna" -exec cp {} /ruta/destino/ \;
```
Luego se generaron scripts para utilizar QUAST para cada uno de los assemblies descargados
```bash
#!/bin/bash  
  
# Directorio de entrada  
input_directory="/media/tobo/files/Tesis/I1_genome_analysis/Assemblies/Bifido_Assembl  
ies"  
  
# Directorio de salida para los resultados de Quast  
output_parent_directory="."  
  
# Número de hilos (threads) para Quast  
threads=32  
  
# Iterar sobre los archivos .fna  
for fna_file in "$input_directory"/*.fna; do  
   # Obtener la base del nombre del archivo sin extensión  
   base_name=$(basename -s .fna "$fna_file")  
  
   # Directorio de salida para el archivo .fna actual  
   output_directory="$output_parent_directory/$base_name"  
  
   # Crear el directorio de salida si no existe  
   mkdir -p "$output_directory"  
  
   # Ejecutar Quast  
   quast.py -o "$output_directory" -t "$threads" "$fna_file"  
done
```
finalmente, se generó el script para extraer los datos útiles para realizar el análisis de la calidad de estos assemblies
#### Codigo

```bash
#!/bin/bash  
  
# Directorio padre donde se encuentran los resultados de Quast  
parent_directory="."  
  
# Archivo donde almacenarás los datos extraídos para el plot  
data_file="datos_quast.txt"  
  
# Encabezado del archivo de datos  
  
# Iterar sobre los subdirectorios  
for result_directory in "$parent_directory"/*/; do  
 if [ -d "$result_directory" ]; then  
# Obtener el nombre del subdirectorio  
   directory_name=$(basename "$result_directory")  
  
   # Ruta completa al archivo report.txt  
   report_file="$result_directory/report.txt"  
  
   # Extraer los valores de los parámetros (ajusta según el formato del archivo repo  
rt.txt)  
   n50_value=$(grep "N50" "$report_file" | awk '{print $2}')  
   n75_value=$(grep "N75" "$report_file" | awk '{print $2}')  
   l50_value=$(grep "L50" "$report_file" | awk '{print $2}')  
   l75_value=$(grep "L75" "$report_file" | awk '{print $2}')  
   largest_contig_value=$(grep "Largest contig" "$report_file" | awk '{print $3}')  
   GC_value=$(grep "GC (%)" "$report_file" | awk '{print $3}')  
   # Imprimir información (opcional)  
   echo "$directory_name $n50_value $n75_value $l50_value $l75_value $largest_contig  
_value" "$GC_value" >> "$data_file"  
 fi  
done

```
#### Codigo
El archivo resultante datos_quast.txt se le agregaron los nombres de las columnas y se generó un archivo tsv el cual se procesó utilizando python.
```python
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("datos_quast.csv", delimiter='\t)
# N50 vs Assembly
plt.subplot(2, 3, 1)
plt.bar(data['Assemblie'], data['N50'])
plt.title('N50')
plt.xticks([])

# N75 vs Assembly
plt.subplot(2, 3, 2)
plt.bar(data['Assemblie'], data['N75'])
plt.title('N75')
plt.xticks([])

# L50 vs Assembly
plt.subplot(2, 3, 3)
plt.bar(data['Assemblie'], data['L50'])
plt.title('L50')
plt.xticks([])

# L75 vs Assembly
plt.subplot(2, 3, 4)
plt.bar(data['Assemblie'], data['L75'])
plt.title('L75')
plt.xticks([])

# Largest Contig vs Assembly
plt.subplot(2, 3, 5)
plt.bar(data['Assemblie'], data['Largestctg'])
plt.title('Largest Contig')
plt.xticks([])

# %GC vs Assembly
plt.subplot(2, 3, 6)
plt.bar(data['Assemblie'], data['GC%'])
plt.title('%GC')
plt.xticks([])

plt.tight_layout()
plt.show()
```
Con esto obtendremos los gráficos para observar el comportamiento de cada una de las variables de Quast. Aunque para analizar la calidad de nuestro ensamble se utilizó la media de cada uno de estos parámetros
#### Assembly Quality plots
![[Pasted image 20231206171624.png]]
#### Codigo

```python
mean_n50 = data['N50'].mean()
mean_n75 = data['N75'].mean()
mean_l50 = data['L50'].mean()
mean_l75 = data['L75'].mean()
mean_largest_contig = data['Largestctg'].mean()
mean_gc = data['GC%'].mean()

print("Media N50:", mean_n50)
print("Media N75:", mean_n75)
print("Media L50:", mean_l50)
print("Media L75:", mean_l75)
print("Media Largest Contig:", mean_largest_contig)
print("Media GC%:", mean_gc)
```
#### Análisis
Los valores obtenidos para estos parámetros son:

Media N50: 339833.27667269437
Media N75: 295166.321880651
Media L50: 34.19168173598553
Media L75: 67.33453887884268
Media Largest Contig: 424446.75768535264
Media GC%: 55.570361663652804
Respecto a nuestro ensamble se obtuvo lo siguiente ![[Pasted image 20231106124351.png]]
N50: 322.889
L50: 3 
Largest contig: 613.951
GC% : 58.67
Mismatches = 0
Por lo tanto, tenemos que nuestro ensamble realizado con SPADES se encuentra por sobre el promedio de los ensambles disponibles, también se confirma el alto %GC de esta especie que coincide con la distribución de la variable en los gráficos anteriores. Respecto a la contigüidad del ensamble, revisaremos la métrica N50 en la cual obtenemos un valor muy cercano al promedio, lo que nos dice que la contigüidad de nuestro ensamble es similar a la de los genomas disponibles en NCBI, incluso si nos fijamos en el criterio L50 obtenemos un valor 10 veces más pequeño que el de los genomas disponibles.
# Annotation
## Functional annotation

# Conclusion




