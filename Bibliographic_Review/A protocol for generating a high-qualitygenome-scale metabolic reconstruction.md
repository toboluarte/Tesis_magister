---
autores: Ines Thiele, Bernhard Ø Palsson
tipo: protocolo
organismos: 
tags:
  - Biblographic_Review
resumido: false
publicado: "2010"
---
# Introducción
La reconstrucción de redes metabólicas se ha convertido en una herramienta indispensable en el estudio de la biología de sistemas de los metabolismos.
Se carece de un protocolo adecuado para el procedimiento en detalle de la construcción de modelos.
En este artículo se presenta un control de calidad para asegurar la calidad de la reconstrucción. En particular este protocolo apunta a la data necesaria para el proceso de la reconstrucción, además se presentan pruebas para verificar la funcionalidad y aplicabilidad de los modelos metabólicos. Finalmente, este protocolo presenta estrategias para debuggear modelos que no funcionan.
Reviews destacan que existen problemas con las bases de datos de anotaciones, por lo que se requiere evaluación manual. En este artículo se describe el proceso de reconstrucción manual.
Las reconstrucciones de eucariotas son más complejas por el tamaño de sus genomas, cobertura del conocimiento de sus compartimientos celular.
La información mínima incluye el acceso a la <mark class="hltr-yellow">secuencia del genoma</mark>, de donde las funciones metabólicas claves pueden ser  obtenidas, y datos fisiológicos como las condiciones de crecimiento que permiten la comparación de las predicciones del modelo con datos experimentales. Adicionalmente, se pueden comparar objetivos celulares, pero no son parte de este protocolo, sin embargo, lo podemos encontrar.[[Predicting biological system objectives de novo from internal state measurements]]
Un gran recurso son los libros específicos de organismos, en casos de que la información sea escasa información de vecinos filogenéticos puede ser de gran ayuda.

# Diseño Experimental
El proceso de reconstrucción descrito en este artículo consiste de 4 pasos utilizados en la etapa 5. El orden es una recomendación y puede ser alterado mientras todas las etapas sean completas, la calidad de la reconstrucción se asocia con llevar a cabo todos estos pasos.
1. Crear una reconstrucción borrador: La primera etapa consiste en la generación de un borrador basado en la anotación del organismo blanco y bases de datos bioquímicas. Esta reconstrucción es una colección de las funciones metabólicas codificadas en el genoma, siendo probable que algunas falten y otras sean incluidas erróneamente. (por anotaciones incorrectas o incompletas). Herramientas como Pathwaytools o metaSHARK pueden ser utilizadas para la reconstrucción del borrador, <mark class="hltr-red">pero no reemplazan la curación manual</mark>.
	1. Anotación genómica: Debemos definir las propiedades de los genes respecto al genoma del organismo, también permite mapear los datos, por ejemplo la expresión génica en estudios posteriores. En algún punto la curación depende principalmente de la anotación genómica, es posible requerir de re anotación de genes, <mark class="hltr-red">pero el procedimiento no es discutido</mark> en este protocolo. [[CDS, ORF Y herramientas de anotación]] 
	2. Funciones metabólicas candidato: Para obtener la reconstrucción borrador, uno puede automáticamente conseguir los genes metabólicos directamente desde la anotación genómica usando palabras claves o categorías de ontología de genes GO. Las reacciones metabólicas catalizadas pueden ser conectadas con el borrador usando los E.C numbers y bases de datos de reacciones bioquímicas como <mark class="hltr-yellow">KEGG</mark> y <mark class="hltr-green">BRENDA</mark>. Es destacable que estas primeras etapas no pretenden tener una lista de candidatos completa o comprensiva, de hecho puede estar llena de falsos positivos, como por ejemplo proteínas involucradas en la metilación del DNA o quinasas, las cuales no tienen un impacto directo en el modelo.
2. Refinamiento manual de la reconstrucción: en esta etapa, el borrador será reevaluado y redefinido. Para cada entrada de gen y reacción, se deben hacer 2 preguntas. <mark class="hltr-blue">¿Debe estar esta entrada aquí?¿Hay alguna entrada faltando para conectar la entrada con la red?</mark> Esta fase del proceso se concentra en la curación y el refinamiento del contenido de la red. En particular, se debe evaluar individualmente cada función metabólica comparándola con literatura específica del organismo. 
    Es recomendado refinar y ensamblar la curación vía por vía, comenzando por las vías canónicas. Las vías periféricas y las reacciones sin un producto metabólico claro deben ser agregadas en un paso posterior
4. 
3.
4.  as
5. 

3.

# Conclusión y Discusiones
