---
autores: Daniel Machado, Sergej Andrejev, Melanie Tramontano and Kiran Raosaheb Patil
tipo: paper
organismos: 
tags:
  - Biblographic_Review
resumido: false
publicado: "2018"
keyword:
---
# Introducción
Relacionar el fenotipo metabólico de un organismo con perturbaciones ambientales y genéticas es el eje de muchas preguntas de investigación. Para este propósito, los modelos metabólicos a escala genómica entregan una base mecanística, permitiendo predecir los efectos de knockouts génicos o cambios nutricionales. De hecho, estos modelos son actualmente usados en una gran cantidad de aplicaciones, incluyendo el diseño racional de cepas para la industria, descubrimiento de drogas para microorganismos patógenos y el estudio de enfermedades con asociaciones a rasgos metabólicos.
Una emergente aplicación de estos modelos es el estudio del cross-feeding y la competencia por nutrientes en comunidades de microorganismos. Sin embargo, las aplicaciones de estos modelos se quedan atrás de la oportunidad presentada por el incremento de sets de datos meta genómicos y genómicos. Uno de los mayores cuellos de botella es el llamado proceso de reconstrucción a escala genómica, el que usualmente requiere curaciones laboriosas y que consumen tiempo, sin esto la calidad de los modelos permanece baja, esto sumado a que las comunidades bacterianas tienen usualmente cientos de especies.
En este artículo se presenta la herramienta CarveMe, la cual implementa una reconstrucción top-down. Este comienza por reconstruir un modelo metabólico universal, el cual es curado manualmente para los problemas mencionados en [[A protocol for generating a high-qualitygenome-scale metabolic reconstruction]].
Entonces, para cada reconstrucción, este modelo se convierte en un modelo específico en un proceso llamado CARVING.
Esencialmente, este proceso remueva las reacciones y metabolitos no predichas para estar en un organismo dado, mientras conserva toda la curación manual y la estructura relevante del modelo original.
Gracias a que es una aproximación top-down permite inferir las capacidades de uptake y secreción de un organismo basado exclusivamente en evidencia génica, haciéndolo especialmente práctico para aquellos organismos que no pueden ser cultivados bajo medios bien definidos. Finalmente, CarveMe automatiza la creación de comunidades microbianas por medio de unir sets de especies individuales en redes a escala comunitaria

## Metodología
CarveMe es un script de Python para construir un modelo metabólico universal por medio de descargar todas las reacciones y metabolitos disponibles en la base de datos de BiGG en un solo archivo SBML. Toda la metadata está guardada como anotaciones SBML
#### Modelo bacteriano universal
El modelo construido desde toda la base de datos de Bigg fue curado manualmente para generar un modelo completamente funcional del metabolismo bacteriano. 
1. Todas las reacciones y metabolitos presentes en compartimiento eucariontes se removieron
2. Una ecuación de biomasa universal fue agregada al modelo (Adaptación de Escherichia coli)
3. Restringir la reversibilidad de las reacciones para eliminar fenotipos termodinámicamente improbables. Los límites superiores de la energía de Gibbs se estimaron utilizando la fórmula clásica de la energía libre.
4. Eliminar las reacciones no balanceadas, si estas no se eliminan, pueden llevar a la generación espontánea de masa. De manera subsecuente, las reacciones bloqueadas y los metabolitos de punto muerto fueron determinadas utilizando FVA (flux variability análisis) y removidas del modelo
5. Finalmente, el modelo se simuló bajo diferentes composiciones de medio, incluyendo medio mínimo M9 con glucosa y medio completo
##### Anotación de genes
Las secuencias aminoácidicas para todos los genes en BiGG fueron descargados de NCBI y agrupados en solo un archivo FASTA. Este archivo se utilizó para alinear el genoma de input dado por el usuario (con DIAMOND) y encontrar los genes homologos en la base de datos de BiGG. 
Se pueden entregar archivos DNA o protein FASTA, notar que la detección de los open reading frame está fuera del scope de esta herramienta.
De manera alternativa, el usuario puede entregar un archivo de alineamiento generado de manera externa con eggnog-mapper, que entrega mayor confianza para la anotación funcional por medio de refinar los alineamientos con predicciones de ortología
# Resultados

# Conclusión y Discusiones
