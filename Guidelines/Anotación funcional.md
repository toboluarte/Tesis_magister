---
tags:
  - Guide_lines
  - Analisis_genomico
  - Anotacion
---
Luego de obtener las anotaciones utilizando prokka [[PROKKA]], las que pueden tener discrepancias con la cantidad de genes contenidas en el organismo en la realidad, como ya lo he escrito [[CDS, ORF Y herramientas de anotación]], es recomendado profundizar en el análisis. Sobre todo haciendo anotaciones funcionales, lo que quiere decir, vincular las anotaciones con otras bases de datos como KEGG, GO, entre otras.
Desde la salida de los archivos de PROKKA obtendremos archivos con extensión GFF y GBK. De estos archivos se puede extraer las secuencias para luego usar blastp. 
Para esto es recomendable instalar blast de manera local al igual que el paquete de herramientas de EMBOSS.
Siguiendo con el proces continuaremos haciendo un retrive de las secuencias presentes en nuestros archivos de anotaciones utilizando <mark class="hltr-yellow">seqret</mark>
```bash
seqret -sformat genbank -osformat fasta -auto -stdout tu_archivo.gbk > tus_proteinas_anotadas.fasta

```
Ahora, si queremos utilizar blast para continuar con nuestros análisis, debemos tener en consideración la descarga de las bases de datos. En este caso en particular se utilizará la base de datos no redundante (nr)
Luego de descargar esta base de datos de 160 GB, procederemos a descomprimirla y luego formatear la base datos
```bash
wget ftp://ftp.ncbi.nlm.nih.gov/blast/db/FASTA/nr.gz
gunzip nr.gz
makeblastdb -in nr -dbtype prot -out nr

```
Debemos ser cuidadosos al escoger los directorios donde vamos a descargar las bases de datos de blast, puesto que deberemos indicarle el directorio en el que están cada vez que las queramos utilizar.
```bash
%también se pueden usar los archivos .faa de prokka
blastp -query prokka.faa -db nr -out resultados_blast.xml -evalue 1e-5 -outfmt 5

```
Con esto contaremos con la homología de las anotaciones, las que nos pueden ayudar a encontrar las funciones, lo cual será útil para la reconstrucción de los modelos [[Metabolic Model Bifidobacterium Breve I1]]
Cabe destacar que estos es un proceso lento, y muy demandante de poder de cómputo por lo que es más conveniente utilizar la siguientes herramientas. Además debemos seleccionar el formato de salida en función de como queremos visualizar los datos 5=XML, que se debe utilizar un visualizardor o hacer parsing de los datos que puede ser más demandante de tiempo.
## Vías metabólicas
Utilizaremos herramientas como KEGG para mapear los genes a vías metabólicas. [[BlastKoala_Relevantes]]

## Ontología Génica
Podemos utilizar InterProScan para agregar información de ontología génica a nuestras anotaciones
## Funciones de Proteínas
Podemos utilizar PFAM para predecir dominios de proteínas y funciones específicas asociadas con estos dominios

Para estas últimas categorías de anotaciones funcionales lo que tenemos que hacer es:
Primero descargar y descomprimir la herramienta interproscan, luego debemos hacer que los hmms se indexen y compilen (revisar tutorial de instalación), una vez hecho lo anterior, debemos darle como archivo de entrada los archivos .faa de la salida de [[PROKKA]]
```bash
./interproscan.sh -i ../../../files/Tesis/Genomas_Tesis/Breve_I1_definitivo/pr  
okka_results/PROKKA_11062023.faa -f gff3 -o resultados_interproscan --cpu 8 -goterms -pa --verbose
```
Sin embargo, la mejor opción para luego tener una buena visualización de los datos es que el output se encuentre en formato JSON, dado que podemos usar el visualizador de EBI https://www.ebi.ac.uk/interpro/result/InterProScan/#table 
```bash
./interproscan.sh -f JSON -i ../../../files/Tesis/Genomas_Tesis/Breve_I1_definitivo/pr  
okka_results/PROKKA_11062023.faa -b resultados_interproscan --cpu 8 -goterms -pa --verbose
```
De esta forma podremos visualizar de mejor manera las anotaciones funcionales.