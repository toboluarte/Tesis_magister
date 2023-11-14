---
tags:
  - Guide_lines
  - Analisis_genomico
publicado: "2019"
---

# Merlin
Para el proceso en concreto utilizaremos MERLIN. Para utilizar este software debemos crear un workspace y conseguir el taxonomy ID de cada una de las especies que queremos reconstruir. En este caso vamos a proceder agregando el ID 1685.
1. Debemos entregarle el genoma a Merlin, este puede ser entregado en un archivo o conectarse a NCBI de manera remota, de hecho cuando agregamos un ID se descargan automáticamente. Las extensiones permitidas son .faa, .fna, .gbff.
2. Cargar data de KEGG: Obtener información metabólica es mandatario para la reconstrucción de modelos metabólicos a escala genómica. Esto lo haremos yendo a la pestaña de model, seleccionaremos la opción load, y luego seleccionaremos KEGG metabolic data y el workspace en la que queremos cargar la data.
3. Cargar datos de anotación genómica: El propósito es asignar funciones metabólicas, los productos génicos y los EC numbers a todas las secuencias codificantes del genoma
	 1. Búsqueda de homología: En MERLIN las anotaciones funcionales provienen de la búsqueda de similitudes en bases de datos remotas como uniprot o swissprot utilizando BLAST, cabe destacar que debido a la dificultad de encontrar el servidor de NCBI con baja carga podemos hacer el BLAST de manera local y cargar el resultado.
![[Pasted image 20231114144600.png]]