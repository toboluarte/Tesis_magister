---
tags:
  - Guide_lines
  - Instalaciones
---

Para manejar la instalación de paquetes y herramientas, es altamente recomendado utilizar miniconda o anaconda.
```bash
wget https://repo.anaconda.com/archive/Anaconda3-2023.09-0-Linux-x86_64.sh 
sh ./Anaconda3-2023.09-0-Linux-x86_64.sh

```
Procederemos con la instalación, y agregaremos el bin a nuestro $PATH modificando el archivo .bashrc.
ahora podemos agregar canales y crear ambientes
```bash
conda config --add channels bioconda
conda config --show channels
conda create -n bioinformatica fastqc %just an example
conda init
conda activate bioinformatica
```
Podremos agregar algunos paquete utiles como prokka, SPADES y QUAST que han sido utilizados.
```bash
conda install -c bioconda spades
conda install -c bioconda prokka
conda install -c bioconda quast
```
