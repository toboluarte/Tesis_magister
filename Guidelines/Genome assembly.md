---
tags:
  - Guide_lines
  - Ensamble_genoma
---
Existen muchos softwares disponibles para ensamblar genomas. Estos son utilizados para "juntar" las lecturas de la secuenciación en contigs, la agrupación de estas lecturas es conocida como k-mers, los que son cadenas de longitud k las que son las unidades fundamentales del ensamblaje de genomas. Gran parte de los algoritmos de ensamblaje están basados en la aproximación de Brujin, los que son estructuras de datos que representan la información de superposición en las secuencias de ADN, siendo cada nodo un k-mer y los bordes representan las superposiciones de k-1 bases.
Luego se utilizan los caminos mínimos dentro de este gráfico para construir los contigs.
Dado que está ampliamente respaldado en bibliografía utilizaremos [[remote_obsidian/Analisis_genoma_Bifido_breve/SPADES]] [[SPADES_2]]
```bash
conda install -c bioconda spades

```