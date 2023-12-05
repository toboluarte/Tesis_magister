---
autores: Robert A. Edwards
tipo: protocolo
organismos: 
tags:
  - Biblographic_Review
resumido: true
publicado: "2016"
keyword:
---

# Introducción
El análisis de balance de flujos FBA, se ha convertido en el método estándar para predecir los flujos de las reacciones en las redes metabólicas. FBA es una optimización lineal basada en restricciones para resolver los flujos de compuestos por medio de redes metabólicas para predecir fenotipos celulares.
Una sola ecuación es incluida en el sistema y representa la función objetivo. En modelos bacterianos suele haber más reacciones que compuestos para describir el sistema.
El proceso de correr FBA puede ser dividido en 2 objetivos amplios. Crear el modelo matemático y resolver el modelo. Siendo la creación del modelo matemático mucho más complejo, dado que requiere la incorporación de conocimiento biológico a la transición de secuencia-roles funcionales-enzimas-reacciones.

## Desde el DNA al FBA
El primer paso es identificar los roles funcionales en el genoma, conectar estos roles a complejos enzimáticos y luego a reacciones, convirtiendo estas reacciones en ecuaciones que describen la conversión de sustratos en productos.
# PyFBA 
Desarrollado en python para poder construir modelos y correr FBA funciona con GLPK o Ilog CPLEX 
# Genome Annotations
El primer paso de construir un modelo es identificar todos los genes presentes en ese organismo. Hay múltiples herramientas de anotación como RAST o [[PROKKA]], BG7, Blast2GO y BASys. Muchos de estos toman contigs no anotados y iteran para definir proteinas y RNAs codificantes para asignar roles funcionales a estos genes.
# Convirtiendo roles funcionales a reacciones
Después de identificar los genes codificantes presentes en el organismo, y asignarles funciones a estas proteinas, los complejos enzimáticos creados por estas proteinas deben ser caracterizados. EC numbers son los más utilizados cuando se hacen estos mapeos entre diferentes repositorios porque son las anotacioines más ampliamente utilizadas para los productos genéticos, sin embargo, los EC numbers no cubren todas las reacciones de los microorganismos.
Los complejos enzimaticos pueden ser formados por uno u múltiples roles funcionales, y cada uno de los roles funcionales puede estar involucrado en uno o más complejos.
Por ejemplo, el rol funcional de la <mark style="background: #FFF3A3A6;">proteina fosfoenolpiruvato fosfotransferasa del sistema PTS</mark> (EC 2.7.3.9) codificada por el gen ptsI puede estar involucrada en múltiples complejos, cada uno asociado con importar un azúcar diferente.
Para convertir roles funcionales enreacciones,s estos roles primero deben estar conectados al complejo enzimático. Si el sistema de anotaciones utilizado para identificar los roles en el genoma solamente entrega EC numbers, estos necesitan estar conectados a complejos. La mayoria de las subunidades del mismo complejo enzimático reciben el mismo EC number.
Las conexiones entre roles funcionales y reacciones o vias pueden ser obtenidas de muchas fuentes como EXPASY, KEGG, METACyc, BRENDA.
# Convirtiendo reacciones a matrices estequiométricas
Un modelo a escala genómica comienza con una lista de ecuaciones, compuestos y compartimientos, y para las soluciones matemáticas podemos convertir eso en una matriz estequiométrica. Esta define el espacio factible de fenotipos que el sistema puede expresar.
# Formulación del medio
Otra restricción es el medio en el que crece el organismo, las recetas casi para todos los medios están disponibles en línea. La única dificultad <mark style="background: #FF5582A6;">es asegurar la correlación entre los nombres de los compuestos usados en la formulación del medio y los nombres de los compuestos utilizados en las reacciones metabólicas</mark>. Una aproximación para superar este obstáculo, es, por ejemplo, usar una base de datos separada de compuestos con ID's únicos. Por  defecto, los compuestos del medio tienen una locación extracelular y la presencia del transportador es requerida para moverlos dentro de la celular; otra restricción en los modelos a escala genómica.
Históricamente, la identificación de proteínas transportadoras es desafiante porque son muy similares (homologas) entre ellas y solo difieren en la especificidad del sustrato.
# Influjo y secreción de medio
Estos modelos requieren que compuestos sean tomados desde el medio extracelular y que ciertos compuestos (deshechos) sean secretados. Además, cada compuesto de la matriz estequiométrica debe estar balanceado para la solución del problema. Estas reacciones son generalmente llamadas drain-flux reactions or external reactions, en PyFBA son llamadas uptake and secretion reactions.
# Límites de las reacciones
Resolver ecuaciones lineales de sistemas infra determinados, un espacio de soluciones tiene que ser dado que limite los parámetros aplicados a cada una de las reacciones. Por lo que cada una de las reacciones de la matriz estequiométrica está controlado por un set de límites que limitan el flujo a través de esa reacción. Muchas veces estos límites entregan la direccionalidad de la reacción
# Límites de compuestos
Un principio central de FBA es asumir que el cambio en la concentración de cada compuesto es igual o balanceada y así la suma de la concentración de los compuestos es 0, a excepción de los compuestos que son tomados o secretados. Este estado de equilibrio de balance de masas permite que el FBa se llevado a cabo sin ninguna información kinetica, y también actua como otra restricción al sistema, para asegurar que el consumo de los compuestos sea igual a la producción.
# Función Objetivo
Una sola función es designada como función objetivo y es incluida a la matriz, generalmente la reacción de la biomasa
# Resolviendo el puzle de programación lineal
Una vez construida la matriz estequiométrica, el medio definido, los límites de las reacciones fijados y una ecuación de biomasa definida u otra función objetivo. El sistema puede ser resuelto por medio de programación lineal.
# Gap-filling
Normalmente un modelo construido desde las anotaciones en un genoma no va a crecer porque la red metabólica está incompleta. Por lo que deben ser agregadas reacciones para asegurar el crecimiento. Un proceso llamado Gap-filling. Este es el punto en el que la mayor cantidad de afirmaciones erróneas respecto al metabolismo de un organismo se hacen
# Conclusión y Discusiones
El modelamiento a escala genomica extiende la utilidad de la anotación de genomas de microorganismos por medio de identficar lo que esta ocurriendo en la célula. La conversión de roles funcionales a reacciones destaca nuestro entendimiento del metabolismo celular, mientras que los gaps que quedan y necesitan ser llenados antes de que el modelo crezca, destacan las áreas en las que tenemos menor comprensión de la bioquímica.
Identificar las reacciones durante el gap-filling lleva a la oportunidad de mejorar la anotacones genómicas. Las regiones donde las secuencias del DNA no se les ha asignado funciones por problemas en el paso de la anotación