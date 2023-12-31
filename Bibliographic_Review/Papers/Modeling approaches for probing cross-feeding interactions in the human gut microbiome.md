---
autores: Pedro Saa, Arles Urrutia, Claudia Silva-Andrade, Alberto J. Martín, Daniel Garrido
tipo: review
tags:
  - Biblographic_Review
resumido: true
publicado: "2021"
---
# Introducción
El RNA16s y los estduios metagenomicos han permitido a los científicos evaluar las estructuras de comunidades como la microbiota humana, principalmente en términos de abundancia relativa de especies (riqueza), intra o inter diversidad y funciones metabólicas.
Se ha hecho avances de comprensión de como se establece la comunidad de la microbiota infantil. 
Las vistas estáticas no consideran todas las interacciones que moldean la composición de una comunidad microbiana compleja como la microbiota intestinal. Con cientos de microorganismos habitando o transitando este ecosistema. Al menos 30.000 interacciones pueden ser contadas en un tiempo específico en la microbiota intestinal, las aproximaciones experimentales solo han logrado estudiar consorcios artificiales hasta 25 especies. Por lo anterior, se genera una brecha considerable en la comprensión de las interacciones, lo que ha generado un creciente interés en las aproximaciones **Top-Down** de la biología de sistemas para simplificar esta complejidad tremenda.
Las interacciones microbianas varían en su especificidad y costos, resultando en diferentes resultados ecológicos. Las interacciones microbio-microbio incluyen el **quorum sensing**, un proceso poco estudiado en la microbiota intestinal. Los estudios genómicos de la microbiota intestinal sugieren que el intestino está dominado por competencia de interferencia, con una alta abundancia de genes produciendo bacteriocinas y **sistemas de secreción tipo 6**.
El humano tiene diferentes formas de modular su microbioma, como las <mark class="hltr-blue">inmunoglobulinas A</mark>, <mark class="hltr-blue">secreciones o péptidos antimicrobianos</mark>. Las fuerzas que influyen en los perfiles del microbioma son desconocidas, sin embargo, no es posible dejar de lado factores como la concentración de oxígeno, movimientos peristálticos y efectores de la inmunidad innata. Además, debemos considerar que la distribución de los microorganismos no es homogénea, de hecho muestran una gradiente de concentración.
El cross-feeding puede ser entendido como el intercambio metabólico entre microorganismos. Siendo el intercambio de ácidos grasos de cadena corta un intercambio común. Otras <mark class="hltr-red">moléculas como amino ácido, vitaminas o</mark> <mark class="hltr-red">ácidos grasos de cadena corta ramificados también participan en el cross feeding metabólico</mark>.
Las interacciones metabólicas de la microbiota intestinal suelen involucrar un carbohidrato complejo y un ácido graso de cadena corta, también se ha observado que algunos aminoácidos participan.
Por ejemplo, <mark class="hltr-purple">los HMOS promueven cross feeding de los productos de la degradación de glicanos entre especies de bifidobacteria</mark>, promoviendo la colonización de especies productoras de butirato.
Los GSMMs son **estructura matemáticas** derivadas de reconstrucciones de redes a escala genómica, descritas por todas las reacciones asociadas con los genes metabolicos en el genoma del organismo. Estos modelos son complementados con data experimental, respecto a la composición celular, capacidades de crecimiento, perfiles de consumo/producción para representar el fenotipo metabólico.
Recientemente, por medio de la integración de datas omicas más profundas y amplias, las aproximaciones de modelamiento, permiten la exploración de hipotesis con diferentes grados complejidad, que además reducen la cantidad de experimentación necesaria y revelando nuevas perspectivas en los mecanismos de las interacciones, sin embargo, hay muchos desafios y oportunidades en este campo. Este review resume los recientes avances en <mark class="hltr-orange">ecología y aproximaciones de modelamiento para estudiar el cross feeding</mark> en la microbiota intestinal.
# Estudios Experimentales de cross feeding
El estudio de las interacciones tipo cross feeding ha crecido por las mejoras en las técnicas de aislamiento de microbios y el deposito en bancos de cultivo, la gran mayoria de las especies del microbioma intestinal son altamente sensibles al oxigeno y presentan requerimientos metabolicos inpredecibles. Un ejemplo es KLE 1738, un aislado intestinal que una <mark class="hltr-green">GABA derivado de bacteroidetes</mark> como fuente de carbono y de energia.
Los experimentos de cross feeding usualmente suelen utilizar microbios que sean faciles de cultivar, trazables, y representativos o relevantes para su ecosistema. Los setup experimentales suelen incluir ensayos microwell, fermentaciones batch y aislados de feca en biorreactores.
Las interacciones metabolicas en la microbiota intestinal suelen involucrar carbohidratos complejos y SCFA, aun que tambien se ha probado que algunos aminoácidos también cumplen el rol.
Bacteroides es una de las especies más estudiadas por su amplia preferencia por glicanos de la dieta como xilano, pectina y almidones. [[Bifidobacteria and Butyrate-producing Colon Bacteria Importance and Strategies for Their Stimulation in the Human Gut]]
El proceso de degradación de estos glicanos suele resultar en interacciones tipo corss feeding. La inulina es un prebiotico, un polimero de fructosa de más de 60 moleculas. Muchos miembros de la microbiota intestinal tienen la maquinaria para su consumo, incluyendo las bifido bacterias, Rosebura, Bacteroides y especies de lactobacilos.
Fructanos derivados de la inulina y SCFa derivados de la fermentación de inulina suelen promover el crecimiento de bacterias productoras de butirato como *Faecalibacterium praunsnitzii*. Esta estimulación esta mediada por acetato y lactato. Otras interacciones de cross feeding están mediadas por el <mark class="hltr-red">formiato y hidrogeno molecular</mark> , los que pueden ser utilizados por arqueas metanogenicas (*Blautia hydrogenotrophica*). Existen funciones complementarias como evidencias expresadas por diferentes bacterias del microbioma humano
# Interacciones metabolicas y modelamiento basado en ecología
El cross feeding difiere de la cooperación verdadera en que la producción de metabolitos <mark class="hltr-red">no representa un costo en el fitness</mark> del productor, por ejemplo, son subproductos o el resultado de la degradación de una macromolécula, por lo que su producción no necesita de energía adicional. La cooperación está asociada con interacciones mucho más dependientes, donde un microorganismo invierte parte de su energía en sintetizar un metablito que es necesario para otro, de manera concomitante recibiendo un beneficio por su producción. Un ejemplo interesante de cooperación verdadera se presenta por *Bacteroides ovatus* un comensal del intestino que degrada múltiples polisacaridos como inulina, amilopectina y xilano. La degradación de inulina por este microorganismo requiere de 2 xilanasas (<mark class="hltr-red">BACOVA_04502/04503</mark>), esta enzima no representa representa un beneficio directo para B. ovatus, sin embargo, la degradación extracelular en un contexto más complejo representa ventajas, lo que no es el comun en <mark class="hltr-blue">bacteroides, los que suelen maximizar la degradación de glicanos intracelularmente</mark>.
Una observación similar se observa en 2 estrategias de degradación de glicanos caracterizadas entre <mark class="hltr-green">Bifidobacterium longum subsp. infantis y Bifidobacterium bifidum</mark>[[Human Milk Oligosaccharides and infant Gut Bifidobacteria Molecular Strategies for their Utilization]]
Estas interacciones entre especies pueden ser clasificadas como cooperación verdadera involucrando la producción de proteinas costosas que benefician a la comunidad. Algunos estudios predicien la cooperación inestable en el estado de equilibrio y <mark class="hltr-red">probablemente no sea dominante en ecosistemas complejos</mark>, <mark class="hltr-blue">sin embargo, existen estudios que desafian esta vision</mark> .
La competencia explotativa es una interacción ecológica predecida entre 773 microorganismos de la microbiota intestinal. En particulas la competencia por sustratos de cross-feeding, como monosacaridos, oligosacaridos y ácidos grasos de cadena cortos es común en la microbiota, aún para microorganismos no relacionados taxonomicamente.
<mark class="hltr-green">La competencia usualmente tiene 2 resultados la partición del nicho o la exclusión competitiva</mark>. Mientras las interacciones de cross feeding están expandidas ampliamente en la microbiota intestinal, in vivo están limitadas por la distancia, por medio de experimentos se cree que un maximo de 15 micrometros es el limite para el cross feeding en medios acuosos, este tipo de estudios subraya la importancia de las limitaciones espaciales para las interacciones ecológicas.
Utilizando modelamiento basado en ecología Wang et al.[[Evidence for a multi-level trophic organization of the human gut microbiome]] predijó 4 niveles troficos iterativos de producción y consumo de metabolitos en la microbiota intestinal. Su analisis comenzo con un modelo manualmente curado de las interacciones microbianas y de las dependencias nutricionales [[Mucin cross-feeding of infant Bifidobacteria y Eubacterium hallii]] que contenia 567 microorganismos del intestino y 235 metabolitos consumidos y secretados por estos microorganismos. Combinados con data metagenomica, se determino el número de sustratos convertidos en metabolitos que alimentaban otras bacterias, una parte de estos metabolitos se utilizaba para producir biomasa y otra parte pasaba para el siguiente nivel trófico. Una conclusión de este estudio es que la competencia a nivel de genero puede explicar la diversidad taxonomica del microbioma.
Esta plataforma ecológica ha sido recientemente combinada con métodos de machine-learning para predecir nuevas interacciones metabolicas no exploradas en el microbioma intestinal. <mark class="hltr-yellow">GutCP (the gut cross-feeding predictor)</mark> este algoritmo ha mejorado la red original, reduciendo el error entre prediccion y datos reales agregando nuevos vinculos de consumo. [[Ecology-guided prediction of crossfeeding interactions in the human gut microbiome]]
# Modelos metabolicos estequeometricos a escala genómica
## Reconstrucción de redes a escala genómica
Se refiere a la colección de reacciones catalizadas por enzimas codificadas por genes de función conocida encontradas en genoma de un organismo.
1. Comienza con la anotación del genoma de los organismos: Se identifican las relaciones Gen-Proteina-Reaccion, que vinculan el genotipo con fenotipo[[A protocol for generating a high-qualitygenome-scale metabolic reconstruction]]
2. Utilización de herramientas de gap filling: Carve me, Metage2Metabo
## Modelos metabolicos a escala genómica y métodos basados en restricciones
COBRA tool box
OptCom
d-OptCom
Steadycom