---
tags:
  - Biblographic_Review
autores: Daniel Garrido, Pamela Veronica Ortuzar, Daniel A. Medina., Fransisco Pinto
organismos: E.coli, B. infantis, B. vulgatus, L. acidophilus
---
## Introducción
El microbioma sufre múltiples cambios a lo largo de la vida de los individuos.
El establecimiento de la microbiota intestinal en el comienzo de la vida es una sucesión programada de microorganismos, es interesante recalcar que, los patrones iniciales de la colonización parecen estar relacionados con la salud en etapas tardías de la vida.

Es relevante la dieta en las primeras etapas, en particular, sobre todo pensando en la etapa de amantamiento, donde la leche materna entrega nutrientes y promueve una microbiota dominada por *Bifidobacterium* [[Human Milk Oligosaccharides and infant Gut Bifidobacteria Molecular Strategies for their Utilization]]
Se vuelve a recalcar que la predominancia es explicada por la gran cantidad de HMOS.
El microbioma puede ser considerado como un biorreactor microbiano, que está continuamente fermentando sustratos de la dieta complejos que no son absorbidos en el **intestino delgado**, como polisacáridos y proteínas.
Los ácidos grasos de cadena corta son productos importantes de fermentación. Los ratios de producción en los adultos son 60:20:20 (acetato, propionato y butirato).

Las heces de los infantes amamantados están caracterizadas por tener altas concentraciones de acetato y lactato.
El complemento para los estudios experimentales que pretenden estudiar las funciones del microbioma intestinal son los modelos matemáticos que explican el comportamiento de cada sistema. Estos incluyen modelos basados en ecuaciones diferenciales y **modelos metabólicos a escala genómica**[[]]. Los GSMM son útiles para determinar los requerimientos nutricionales de los microorganismos, dado que entregan una representación completa del metabolismo celular. En resumen para predecir **cross-feeding** (Magnúsdóttir et al, 2016). Se ha demostrado que ecuaciones de crecimiento simple que incluyen interacciones metabólicas pueden explicar y predecir la composición y la actividad de un consorcio de especies del microbio intestinal de un infante (Pinto et al, 2017), estas interacciones metabólicas pueden ser la inhibición o cooperación (cross-feeding), y están normalmente mediadas por productos de degradación de macromoléculas o ácidos grasos de cadena corta.
## ¿Qué hicieron?
**Análisis de expresión génica:** Se extrajo RNA de los cultivos, te transcribió a cDNA 

**Desarrollo de un modelo matemático:** Se desarrolló un modelo basado en el balance de ecuaciones general en cultivo continuo, pero incorporando interacciones metabólicas como un término adicional a la **ECUACIÓN DE MONOD**, este modelo permite el crecimiento de múltiples especies.
Como input, este modelo tiene las abundancias de cada microorganismo, la concentración de acetato y lactato producido y la cantidad de sustrato consumido en cada condición.

**Cuantificación de abundancia por medio de qPCR**: 
Cuantificación de carbohidratos en los sobrenadantes:
**Experimentos de biorreactor:** 2 fermentaciones continuas independientes se hicieron en un biorreactor de 250 mL 
## Resultados principales
**Switch Dieta:**
El cambio desde fructo oligosacáridos (FOS) a 2-Fucosil lactosa (2FL) de un consorcio compuesto por *E. coli, L. acidophilus, B. infantis, B. vulgatus*, produjo una baja considerable en la biomasa que se estabilizó a un OD=4, las abundancias relativas se conservaron, sin embargo, luego de 18 H se observó un incremento de *B. infantis*, esto fue acompañado por un decremento de *L. acidophilus* y un incremento de *E. coli*. *B. vulgatus* no presentó un incremento relevante en ninguna fase.
**Perfil de Expresión**:
Para el lactobacilo presente en el consorcio se observó un incremento de 15 veces en un gen que expresa una fructoquinasa, la cual se redujo a niveles basales durante la transición a 2FL. Por otro lado, la bifidobacteria mostró la expresión de un Alpha fucosidasa incrementada en conjunto galactosidasa. Sorprendentemente, coli mostró la expresión de una fucosa permeasa, sugiriendo que podría utilizar la fucosa en el medio.
**Modelamiento Matemático:**
Logró capturar los cambios en el crecimiento al cambiar el sustrato.
## Conclusión 
No es tan trivial probar que al cambiar los sustratos disponibles se producen cambios en las abundancias relativas
