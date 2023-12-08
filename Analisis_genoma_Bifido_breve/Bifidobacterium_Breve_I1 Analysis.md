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
Las lecturas fueron extraidas de un proyecto de secuenciación previo.
## Quality Control
Para el control de calidad de estas lecturas se utilizo FASTQC.  En general siendo la calidad de las lecturas aceptables para continuar el análisis. Además, cabe destacar que se observó que las lecturas se encontraban sin adaptadores, por lo que es altamente probable que se tratasen de lecturas previamente procesadas.
# Trimming
Dado que no existian adaptadores en las lecutras este paso fue descartado.
## Quality Control
# Assembly
El ensamblaje de las lecturas se realizó con el software SPADES
## Quality Control
Para realizar el control de calidad se utilizó el programa QUAST, para esto se generaron scripts para descargar todos los assemblies disponibles en NCBI de Bifidobacterium_Breve y crear plots para cada uno de los criterios de contiguidad de relevancia que entrega el algoritmo QUAST.
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
#### Assembly Quality plots for Bifidobacterium_Breve
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

| Criterio de contiguidad/información | All B. Breve assemblies | Lab Sample I1 |     |
| ----------------------------------- | ----------------------- | ------------- | --- |
| N50                                 | 339833.27               | 322889        |     |
| N75                                 | 295166.321              | No Value      |     |
| N90                                 | No value                | 140938        |     |
| L50                                 | 34.19                   | 3             |     |
| L75                                 | 67.33                   | No Value      |     |
| L90                                 | No value                | 8             |     |
| Largest Contig                      | 424446.75               | 613951        |     |
| %GC                                 | 55.57                   | 58.67         |     |


![[Pasted image 20231106124351.png]]
Fig X. Reporte extensivo de Quast para el ensamble del genoma de Bifidobacterium Breve I1

El ensamble realizado con SPADES de las lecturas realizadas en el laboratorio se encuentra por sobre el promedio de los ensambles disponibles en NCBI en múltiples criterios de contiguidad (N50, L50 y Largest Contig). También se confirma el alto contenido GC de esta especie, lo que coincide con la información disponible bibliográficamente. 
# Annotation
Utilizando el ensamblaje obtenido, en una primera instancia se realizaron las predicciones de CDS y anotaciones con el software PROKKA.
Se anotaron 2151 genes de los cuales con el propósito de este análisis destacan las siguientes categorias vínculadas a la utilización de carbohidratos:
**ABC transporters: 22**
	BDNALMGG_00081 putative ABC transporter ATP-binding protein
	BDNALMGG_00209 putative ABC transporter ATP-binding protein YknY
	BDNALMGG_00563 putative ABC transporter ATP-binding protein YbiT
	BDNALMGG_00593 putative ABC transporter ATP-binding protein YlmA
	BDNALMGG_00722 putative glutamine ABC transporter permease protein GlnP
	BDNALMGG_00723 putative glutamine ABC transporter permease protein GlnP
	BDNALMGG_00725 ABC transporter glutamine-binding protein GlnH
	BDNALMGG_00893 putative glutamine ABC transporter permease protein GlnM
	BDNALMGG_00894 ABC transporter glutamine-binding protein GlnH
	BDNALMGG_00978 putative ABC transporter ATP-binding protein
	BDNALMGG_00979 putative ABC transporter ATP-binding protein
	BDNALMGG_01210 ABC transporter ATP-binding protein YtrE
	BDNALMGG_01422 putative ABC transporter ATP-binding protein YknY
	BDNALMGG_01532 ABC transporter glutamine-binding protein GlnH
	BDNALMGG_01785 putative ABC transporter ATP-binding protein YknY
	BDNALMGG_01977 putative ABC transporter ATP-binding protein YknY
	BDNALMGG_01996 putative ABC transporter ATP-binding protein
	BDNALMGG_02000 putative ABC transporter ATP-binding protein
	BDNALMGG_02001 Fatty acid ABC transporter ATP-binding/permease protein
	BDNALMGG_02012 putative ABC transporter ATP-binding protein
	BDNALMGG_02025 putative ABC transporter ATP-binding protein
	BDNALMGG_02026 putative ABC transporter ATP-binding protein
**Hidrolasas: 16**
	BDNALMGG_00072 Pyrimidine-specific ribonucleoside hydrolase RihA
	BDNALMGG_00456 RNA pyrophosphohydrolase  
	BDNALMGG_00577 Choloylglycine hydrolase  
	BDNALMGG_00585 Aminopyrimidine aminohydrolase  
	BDNALMGG_00654 Atrazine chlorohydrolase  
	BDNALMGG_00833 Peptidyl-tRNA hydrolase  
	BDNALMGG_00873 Sucrose-6-phosphate hydrolase BDNALMGG_00970 Pyrimidine-specific ribonucleoside hydrolase RihA  
	BDNALMGG_01059 GTP cyclohydrolase 1  
	BDNALMGG_01193 Deoxyguanosinetriphosphate triphosphohydrolase-like protein  
	BDNALMGG_01453 Phosphoribosyl-AMP cyclohydrolase  
	BDNALMGG_01558 Bifunctional (p)ppGpp Synthase/hydrolase RelA  
	BDNALMGG_01559 Deoxyuridine 5'-triphosphate nucleotidohydrolase  
	BDNALMGG_02029 Gamma-glutamyl-hercynylcysteine sulfoxide hydrolase  
	BDNALMGG_02177 2-hydroxy-6-oxononadienedioate/2-hydroxy-6-oxononatrienedioate hydrolase  
	BDNALMGG_02200 putative Nudix hydrolase NudL
**Glicosilasas: 6**
	BDNALMGG_00243 Biosynthetic peptidoglycan transglycosylase  
	BDNALMGG_00638 Endolytic murein transglycosylase  
	BDNALMGG_00786 DNA-3-methyladenine glycosylase 1  
	BDNALMGG_00915 Uracil-DNA glycosylase  
	BDNALMGG_01136 Biosynthetic peptidoglycan transglycosylase  
	BDNALMGG_01145 Adenine DNA glycosylase
**Glucosidasas: 8**
	BDNALMGG_00306 Oligo-1,6-glucosidase  
	BDNALMGG_00310 Bifunctional beta-D-glucosidase/beta-D-fucosidase  
	BDNALMGG_00469 Thermostable beta-glucosidase B  
	BDNALMGG_00505 Oligo-1,6-glucosidase  
	BDNALMGG_01028 Oligo-1,6-glucosidase  
	BDNALMGG_01206 Oligo-1,6-glucosidase  
	BDNALMGG_01266 Bifunctional beta-D-glucosidase/beta-D-fucosidase  
	BDNALMGG_01613 Beta-glucosidas
**Fucosidasas: 2**
	BDNALMGG_00310 Bifunctional beta-D-glucosidase/beta-D-fucosidase  
	BDNALMGG_01266 Bifunctional beta-D-glucosidase/beta-D-fucosidase
**Galactosidasas: 6**
	BDNALMGG_00021 Beta-galactosidase BgaB  
	BDNALMGG_00436 Beta-galactosidase  
	BDNALMGG_00500 Alpha-galactosidase  
	BDNALMGG_01177 Beta-galactosidase III  
	BDNALMGG_01735 Beta-galactosidase  
	BDNALMGG_02018 Beta-galactosidase LacZ

Estas anotaciones fueron utilizadas para profundizar el análisis utilizando el software dbCAN, especializado en anotar enzimas activas en carbohidratos.
## Functional annotation

# Conclusion




