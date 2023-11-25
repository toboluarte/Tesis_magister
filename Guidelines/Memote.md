---
tags:
  - Guide_lines
  - Control_calidad
---
Al igual que cuando estamos evaluando la calidad de las secuencias, debemos evaluar la calidad de nuestros modelos, tanto como el modelo inicial y los modelos a medida que van siendo curados.
Para esto existe la herramienta memote 
```bash
pip install memote
memote report snapshot --filename "model_report.html" path/tothe/model.xml
```
Utilizando estos comandos podremos generar un reporte de calidad de los modelos en formato HTML al igual que el software fastqc
[memote](https://memote.readthedocs.io/en/latest/getting_started.html). Debemos destacar también que se pueden realizar comparaciones entre 2 modelos, así podemos ir corroborando si las modificaciones realizadas mejoran o emperoan el modelo desde el punto de vista de la consistencia.
