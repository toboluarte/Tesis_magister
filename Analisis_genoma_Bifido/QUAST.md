---
tags:
  - Analisis_genomico
  - Control_calidad
  - Ensamble_genoma
---
Dado que la calidad [[FASTQC]] eran aceptable se procedió a ensamblar el genoma utilizando [[SPADES]] y evaluando la calidad del ensamble genomico utilizando la herramienta QUAST

```bash
quast.py -o ./QuastResults -g prokka_results/PROKKA_11062023.gff -t 8 -1 I1_S39  
0_L004_R1_001.fastq.gz -2 I1_S390_L004_R2_001.fastq.gz --gene-thresholds 0,1000 Assembly_I1_Def/contigs.fasta --glimmer
```


![[Pasted image 20231106124351.png]]

Podemos observar que el tamaño del genoma calza con el descrito en bibliografía, al igual que el porcentaje GC, elevado. [[Bifidobacteria and Butyrate-producing Colon Bacteria Importance and Strategies for Their Stimulation in the Human Gut]]
