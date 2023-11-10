---
tags:
  - "#Analisis_genomico"
  - "#Guide_lines"
---
## Definición
La filogenómica pretende inferir las relaciones evolutivas a nivel genómico. Sin embargo puede resultar un poco desviado de la realidad decir que es a nivel genómico, dado que no es posible utilizar todos los genomas que nos interesan, más bien es una disciplina que pretende acercarse más al nivel genómico que utilizar filogenias basadas en un **gen individual** como el RNA 16S.
En concreto se compran multiples genes concatenados asumiendo que estas relaciones evolutivas inferidas nos entregan información relevante relativa a las relaciones evolutivas entre los genomas analizados.
# Genes de copia única centrales
SCG, son genes que están presentes en 1 copia en la mayoria de los organismos que nos interesan.
# Resumen del proceso
Supongamos que tenemos los genomas que queremos incluir en el proceso y, además tenemos el set de **SCG** que deseamos considerar como blanco.
+ Identificar nuestros genes blanco en todos los genomas considerados.
+ Alinear cada set de genes identificados individualmente
+ Agrupar los alineamientos de manera horizontal
+ Inferir relaciones evolutivas de estas secuencias combinadas (**árbol filogenético**)
![[Pasted image 20231109131639.png]]
°|


# Hands on tutorial
Primero debemos instalar la herramienta que va a ser utilizada "GtoTree"
Para esto podemos utilizar el siguiente comando, que realizara la instalación por medio de anaconda:
```bash

conda create -y -n gtotree -c conda-forge -c bioconda -c defaults -c astrobiomike gtotree
conda activate gtotree

```
Luego de que ya tenemos instalada la herramienta tendremos que generar la lista de genomas que queremos considerar.
Para esto utilizaremos la base de datos de NCBI assembly para utilizar buscar los últimos ensambles de genomas completos.
![[Pasted image 20231109172820.png]]
Ademas con la opción send tu descargaremos una tabla resumen que será de mucha utilidad para poder utilizar **gtotree**
Luego el archivo descargado de esta query que también puede realizarse por linea de comando utilizando la herramienta esearch. Obtendremos una lista de códigos GCA, mediante comandos bash podemos obtener un archivo de texto separado para poder obtener los códigos GCF que son los que utilizara el programa.
```bash
tail -n +2 assembly_result.txt | cut -f 3 > species_accesion.txt

```
Luego de esto si no lo hemos hecho antes debemos descargar los assemblies.
```bash 
GToTree -a Bifidobacterium_Breve_I1_accessions.txt -f our_genome_fasta_files.txt -H Bac  
teria -t -L Species -j 8 -o GTotree-out
```
Finalmente podemos utilizar la herramienta de visualización Itol 
