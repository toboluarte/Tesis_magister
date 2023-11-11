---
tags:
  - Analisis_genomico
  - Anotacion
---

```bash
prokka --outdir ../prokka_results --genus 'Bifidobacterium' --cpus 8 contigs.fasta
```

**Interesting Anottated:**
En total se anotaron 2151 genes
De los cuales nos interesa destacar las siguientes categorías
ABC transporters: 22
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

Hidrolasas: 16
	BDNALMGG_00072 Pyrimidine-specific ribonucleoside hydrolase RihA
	BDNALMGG_00456 RNA pyrophosphohydrolase  
	BDNALMGG_00577 Choloylglycine hydrolase  
	BDNALMGG_00585 Aminopyrimidine aminohydrolase  
	BDNALMGG_00654 Atrazine chlorohydrolase  
	BDNALMGG_00833 Peptidyl-tRNA hydrolase  
	BDNALMGG_00873 Sucrose-6-phosphate hydrolase  
	BDNALMGG_00970 Pyrimidine-specific ribonucleoside hydrolase RihA  
	BDNALMGG_01059 GTP cyclohydrolase 1  
	BDNALMGG_01193 Deoxyguanosinetriphosphate triphosphohydrolase-like protein  
	BDNALMGG_01453 Phosphoribosyl-AMP cyclohydrolase  
	BDNALMGG_01558 Bifunctional (p)ppGpp Synthase/hydrolase RelA  
	BDNALMGG_01559 Deoxyuridine 5'-triphosphate nucleotidohydrolase  
	BDNALMGG_02029 Gamma-glutamyl-hercynylcysteine sulfoxide hydrolase  
	BDNALMGG_02177 2-hydroxy-6-oxononadienedioate/2-hydroxy-6-oxononatrienedioate hydrolase  
	BDNALMGG_02200 putative Nudix hydrolase NudL

Glicosilasas: 6
	BDNALMGG_00243 Biosynthetic peptidoglycan transglycosylase  
	BDNALMGG_00638 Endolytic murein transglycosylase  
	BDNALMGG_00786 DNA-3-methyladenine glycosylase 1  
	BDNALMGG_00915 Uracil-DNA glycosylase  
	BDNALMGG_01136 Biosynthetic peptidoglycan transglycosylase  
	BDNALMGG_01145 Adenine DNA glycosylase
Glucosidasas: 8
	BDNALMGG_00306 Oligo-1,6-glucosidase  
	BDNALMGG_00310 Bifunctional beta-D-glucosidase/beta-D-fucosidase  
	BDNALMGG_00469 Thermostable beta-glucosidase B  
	BDNALMGG_00505 Oligo-1,6-glucosidase  
	BDNALMGG_01028 Oligo-1,6-glucosidase  
	BDNALMGG_01206 Oligo-1,6-glucosidase  
	BDNALMGG_01266 Bifunctional beta-D-glucosidase/beta-D-fucosidase  
	BDNALMGG_01613 Beta-glucosidas
Fucosidasas: 2
	BDNALMGG_00310 Bifunctional beta-D-glucosidase/beta-D-fucosidase  
	BDNALMGG_01266 Bifunctional beta-D-glucosidase/beta-D-fucosidase
Galactosidasas: 6
	BDNALMGG_00021 Beta-galactosidase BgaB  
	BDNALMGG_00436 Beta-galactosidase  
	BDNALMGG_00500 Alpha-galactosidase  
	BDNALMGG_01177 Beta-galactosidase III  
	BDNALMGG_01735 Beta-galactosidase  
	BDNALMGG_02018 Beta-galactosidase LacZ

Como podemos observar existen múltiples genes asociados a la ruptura de carbohidratos lo que está respaldado por bibliografía [[Bifidobacteria and Butyrate-producing Colon Bacteria Importance and Strategies for Their Stimulation in the Human Gut]]
