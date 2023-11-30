---
tags:
  - Model_generation
  - Guide_lines
---
Primero me gustaría reparar en la instalación de esta herramienta la que puede ser problemática para algunos casos, sobre todo si es que deseamos utilizar como optimizador Gurobi.
```bash
conda create -n carveme python=3.9

```
Lo primero relevante a destacar es hacer un ambiente con la versión de Python adecuada, luego debemos activar este ambiente y luego instalar el paquete de Python en conjunto con diamond 
```bash
pip install carveme
conda install -c bioconda diamond
```
En paralelo debemos realizar la instalación del software de optimización, en nuestro caso gurobi, el cual conviene instalar de manera global. [gurobi](https://www.gurobi.com/downloads/gurobi-software/)
Es recomendable llevar este software al directorio /opt/ en caso de los usuarios de linux
```bash
sudo mv ./gurobi.tar.gz /opt/
sudo tar xvfg gruorbi.tar.gz

```
Luego debemos agregar el bin y lib a nuestro .bashrc.
```bash
export PATH="/opt/gurobi/gurobi1003/linux64/bin:$PATH"
export LD_LIBRARY_PATH="/opt/gurobi/gurobi1003/linux64/lib:$LD_LIBRARY_PATH"
```
Luego se debe obtener la licencia utilizando el comando grbgetkey. Notar que esto puede ser solo ejecutado utilizando la red de la institución que tiene la licencia aprobada, de lo contrario no funcionara.
Por último, debemos notar que si intentamos correr algún comando dentro del ambiente creado, nos dirá que hay un problema con carve, particularmente el archivo __initpy__. Esto es porque el código por defecto estará buscando el solver de IBM.
Para esto deberemos cambiar alguno de los códigos.
```bash
subl ~/miniconda3/envs/carveme/lib/python3.9/site-packages/carveme/config.cfg
```
Utilizando sublimetext (se puede utilizar cualquier editor de texto), cambiaremos la línea 23, el parámetro "default_solver" por "gurobi".
Luego deberemos cambiar un par líneas de código en el script de carve
```bash
subl ~/miniconda3/envs/carveme/lib/python3.9/site-packages/carveme/reconstruction/carving.py
```
Aquí deberemos eliminar en la línea 8 la importación después de la ","
y todo el if statement de la línea 181. 

Para generar un modelo debemos seguir las instrucciones de instalación en [[Setup Config]], debemos considerar que se deben instalar múltiples paquetes y además tener el acceso a un solver. 
```bash
carve ./PROKKA_11062023.faa --cobra -o /run/media/arturo/files/Tesis/  
Modelos/bifidobacterium_breve/bifidobacterium_breve_I1.xml --universe grampos --reference /run/media/arturo/files/Te  
sis/Modelos/Bifidobacterium_breve_UCC2003_NCIMB8807.xml -g M9[-O2] --solver gurobi 
%con este comando haremos un modelo sin utilizar como referencia le modelo de agora

carve ./PROKKA_11062023.faa --fbc2 -o ./bifidobacterium_breve_I1.xml --universe grampos --reference /Bifidobacterium_breve_UCC2003_NCIMB8807.xml -g M9[-O2]
```

