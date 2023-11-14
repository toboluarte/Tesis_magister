---
autores: Wang T., Goyal A, Dubinkina V, Maslov S, Tikihonov M
tipo: paper
organismos: 
tags:
  - Biblographic_Review
publicado: "2021"
resumido:
---

# Introducción
El microbioma juega un rol importante en la salud humana, la habilidad de manipularlo tiene un inmenso potencial de prevenir y curar múltiples enfermedades. El microbioma no solo contiene miles de especies, sino que también contiene miles de metabolitos que son consumidos y secretados en un fenómeno que es llamado <mark style="background: #BBFABBA6;">CROSS FEEDING</mark>. Estos metabolitos por los cuales los microorganismos interactúan median interacciones entre especies que pueden impactar directamente al anfitrión, de hecho los niveles de metabolitos son mejor predictor de salud que la distribución de especies.
Un marco de trabajo prometedor es generar un modelo mecanístico del microbioma que pueda conectar los niveles de especies con los metabolitos cuantitativamente.
<mark style="background: #ABF7F7A6;">Un paso esencial es comprender cuáles son las interacciones relevantes en el microbioma intestinal humano</mark>, de hecho inferir interacciones de cross-feeding es un campo relevante y activo en la investigación del microbioma.
Los autores creen que el modelo ecológico de consumo de recursos, propuesto por Tilman [[Consumer-Resource theroy]] entregan los medios por los cuales se pueda generar un bootrapping y predecir nuevas interacciones con sentido ecológico de cross feeding. Además, consideran que esta metodología se puede beneficiar por los avances del machine learning, el cual es efectivo al momento de identificar patrones en datos conocidos y utilizarlos para generar patrones.
En este artículo se propone GUTCP, una abreviatura para cross-feeding predictor: a new, general, and ecology-guided method to infer and predict cross-feeding in the human gut microbiome. Este algoritmo incorpora técnicas de machine learning. 
# Resultados

Revisión del algoritmo propuesto: Depende de un set curado manualmente de interacciones de cross-feeding, luego utiliza las interacciones conocidas para seguir un flujo de metabolitos a través del intestino, en cada paso (en cada nivel trófico), los metabolitos disponibles son utilizados por los organismos que son capaces de consumirlos y una fracción de estos compuestos son secretados como subproductos. <mark style="background: #ADCCFFA6;">Estos subproductos se vuelven disponibles para el consumo de otro set de especies en el siguiente nivel trófico</mark>. En cierto punto, estos metabolitos se convierten en el metaboloma fecal.
![[Pasted image 20231114173103.png]]

# Metodología

# Conclusión y Discusiones
