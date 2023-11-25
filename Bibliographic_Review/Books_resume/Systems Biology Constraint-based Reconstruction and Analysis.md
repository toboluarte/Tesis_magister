---
autores: Bernhard Ø Palsson
tipo: Libro
organismos: 
tags:
  - Biblographic_Review
resumido: false
publicado: "2015"
keyword:
---

# 1. Introducción
Hace unos 60 años, la promesa de la biología molecular sujetaba que si nosotros sabíamos y entendíamos la función de las moléculas que componen la célula, podríamos entender las células y sus funciones. Hoy, después de la generación de múltiples sets de datos y desarrollo de muchas tecnologías, se comienza la biología de sistemas molecular.
La biología de sistemas está centrada en la naturaleza de las relaciones que conectan a los componentes y en los estados funcionales de las redes bioquímicas. 

## Relación genotipo-fenotipo
Mendel descubrió que hay cuantos de información que pasan de generación en generación que determinan la forma y función de un organismo. Hoy esos cuantos se conocen como genes, el conjunto de genes contenido en un organismo se conocen como genotipo. La forma y función de un organismo se refiere al fenotipo.
La relación entre genotipo y fenotipo es desafiante de recrear y comprender. El primer desafío viene de la necesidad de saber cuáles son todos los productos de los genes, y el segundo desafío dado por la necesidad de entender las consecuencias de las complejas interacciones que pueden formarse entre productos de genes.
Hoy, con el desarrollo de múltiples herramientas y los datos genómicos, es posible la formulación de relaciones mecanísticas entre el genotipo y el fenotipo.
## Conceptos de la ciencia a escala genómica

![[Pasted image 20231123164504.png|400]]
En una célula bacteriana, alrededor de 2.5 millones de proteínas funcionan de manera coherente. 10.000 ribosomas y 1.000 tRNA están sintetizando proteínas, múltiples polimerasas están sintetizando el mensaje a ser traducido. Todo esto ocurriendo en el volumen de micrón cúbico. Así, existen incontables de restricciones en estas funciones.
El rango numérico de valores de parámetros que permiten redes así de complejas funcionar coherentemente es muy restricto. A veces, es difícil creer que existe un set de valores de parámetros que permiten el proceso de la vida. La vida es, de hecho, improbable.
Se establece un vínculo entre evolución, causalidad distal y principios de optimización. Las funciones aparecen basándose en una jerarquía, es decir, las nuevas funciones aparecen de las funciones existentes, por lo que comprender la organización jerárquica es clave para comprender las relaciones entre fenotipos y genotipos
## Pensamiento jerárquico
Es necesario adaptar técnicas de pensamiento jerárquico a las propiedades de las redes a escala genómica. Los elementos irreductibles en una red son reacciones químicas elementales. Estas se pueden combinar en mecanismos de reacción, muchas reacciones en módulos o motivos, vías se pueden formar y sectores ser definidos. Actualmente, se depende de definiciones subjetivas u objetivas de los módulos para conceptualizar la jerarquía de la estructura de una red.
## Construyendo principios
Los modelos deben tomar en cuenta la causalidad proximal y distal. Se pueden resumir de manera axiomática los principios para la generación de modelos:
* Todas las funciones celulares están basadas en la química. Los eventos fundamentales dentro de una célula pueden ser descritos por una ecuación química. Estas ecuaciones tienen información relativa a los principios fisicoquímicos.
* Genomas anotados con datos experimentales permiten la reconstrucción de modelos metabólicos a escala genómica. El proceso de reconstrucción es un ensamble a gran escala de información, el cual lleva a una base de conocimientos que es la colección de datos bioquímicos, genéticos y genómicos establecidos representados por la reconstrucción de una red.
* Las células operan bajo una variedad de restricciones, las cuales pueden ser categorizadas en 4 categorías principales.
	* Restricciones fisicoquímicas
	* Topológicas (crowding molécular e impedimento estérico)
	* Ambientales
	* Regulatorias (restricciones autoimpuestas por el sistema)
* Las células funcionan de manera contexto específica: En cada contexto, las células expresan un sub set de genes. Esta data puede ser mapeada para abordar la condición particular. Esto introduce la relevancia del ambiente en la relación del genotipo con el fenotipo.
* La energía y la masa es conservada: S*V =0 
* Las células evolucionan bajo una determinada presión selectiva en un ambiente dado. Sí conocemos la presión selectiva, podemos generar la función objetivo y determinar los estados óptimos dada una red.
Todos los axiomas anteriores juntos son la base conceptual de la reconstrucción y análisis basado en restricciones (COBRA).
# Network Reconstruction: The Concept
Las reconstrucciones están basadas en matrices estequiométricas que contienen los coeficientes que cuentan las moléculas que son consumidas y las que son producidas. Esto permite que la escritura matemática de la red sea solo una, pero las representaciones sean muchas.
## Reconstrucción de una vía
Una red tiene nodos que consisten en compuestos y enlaces que están hechos de las reacciones entre ellos. En su forma más simple, la glicolisis tiene 12 metabolitos primarios, 5 moléculas cofactores (ATP,ADP,AMP,NAD,NADH), Pi, H+ y agua. Son 20 compuestos que participan en la vía.
Los enlaces son las reacciones glucolíticas, 21 incluyendo las reacciones de transporte.
## Reconstrucción de un módulo
Como se había mencionado anteriormente, esto guarda relación con el siguiente nivel de organización de las reacciones, se podría definir como una estructura de información donde se encuentran conjuntos de vías agrupadas.
# Network Reconstruction The Process
## Construir bases de conocimiento
Una reconstrucción basada en un enfoque bottom-up es una anotación en 2 dimensiones de un genoma. Esta incluye una lista de componentes (filas) y los enlaces entre estos componentes (columnas).
Existen similitudes en el proceso de reconstrucción con el ensamblaje de un genoma, principalmente porque existe un solapamiento de estructuras de mayor complejidad, en cuanto a información, en el caso del ensamblaje de genomas, se sobrelapan secuencias cada vez más largas formando los contigs. En el caso de la reconstrucción de redes metabólicas se comienza desde una reacción química, luego una vía metabólica, luego las vías un mapa metabólico y finalmente estas reconstrucciones deben pasar por un gapfilling.
### La Reconstrucción es un proceso de 4 pasos
* Primero, se construye un draft automático, basado en anotaciones de secuencias del organismo blanco e información asociada.
* Datos detallados bioquímicos, genéticos y fisiológicos son utilizados para completar y curar la reconstrucción.
* La reconstrucción es convertida en un formato matemático formando una base de datos de conocimiento a la cual se le pueden hacer consultas respecto a las funciones celulares.
* Las reconstrucciones son validadas contra muchos data sets que pueden llevar a un loop iterativo e incluir una comparación módulo a módulo.
#### Draft Reconstruction
El primer paso es enumerar los componentes de la red. La lista de componentes puede ser obtenida de la secuencia genómica anotada. Para metabolismos, uno recolecta una lista de todos los ORFs que están asociados con enzimas o complejos enzimáticos que catalizan transformaciones metabólicas.
#### Curación manual
Las enzimas identificadas en la secuencia genómica, son identificadas basándose en experimentos de clonación o por homología o análisis de similitud.
En el paso de la curación manual requiere de la examinación del modelo borrador en gran detalle e inorporar información de múltiples fuentes.
Agregar nuevas reacciones es un proceso de 5 etapas: Las que pueden ser revisadas en [[A protocol for generating a high-qualitygenome-scale metabolic reconstruction]]
 



# Metodología
# Resultados

# Conclusión y Discusiones
