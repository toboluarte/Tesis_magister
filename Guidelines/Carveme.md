---
tags:
  - Model_generation
  - Guide_lines
---
Para crear un modelo debemos seguir las instrucciones de instalación en [[Setup Config]], debemos considerar que se deben instalar múltiples paquetes y además tener el acceso a un solver. 
```bash
carve ./PROKKA_11062023.faa --cobra -o /run/media/arturo/files/Tesis/Modelos/bifidobacterium_breve --universe grampos --reference /run/media/arturo/files/Tesis/Modelos/bifidobacterium_breve/Bifidobacterium_breve_UCC2003_NCIMB8807.xml -g M9[-O2] --solver gurobi 
```