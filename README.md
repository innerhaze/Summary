# Summary

---
title: "Relación entre divergencia evolutiva y conectividad histórica en los páramos andinos del norte durante el Pleistoceno: El caso de Espeletiinae"
author: ""
date: ""
output: 
  html_document:
    toc: true
    toc_depth: 3
    toc_float:
      collapsed: false
      smooth_scroll: true
      position: "left"
    theme: flatly
    highlight: tango
---

```{=html}
<style>
/* Mantiene la misma fuente para los blockquotes */
blockquote {
    font-family: inherit; /* Usa la misma fuente que el resto del texto */
    font-size: inherit; /* Usa el mismo tamaño de fuente que el resto del texto */
}

/* Ajusta el ancho del menú de la tabla de contenido flotante */
.tocify {
    width: 1300px; /* Ajusta este valor según sea necesario */
}
.tocify-wrapper {
    width: 1300px; /* Ajusta este valor según sea necesario */
}
</style>
```

------------------------------------------------------------------------

# **1. Introducción**

Este estudio explora la diversificación de los organismos en los páramos de los Andes del norte, un ecosistema de alta montaña que ha sido significativamente influenciado por eventos geológicos y climáticos durante el Pleistoceno. Durante esta época, las fluctuaciones climáticas generaron dinámicas complejas de conectividad entre los fragmentos de páramo, lo que se hipotetiza que afectó la distribución y divergencia de las especies que habitan estos ecosistemas. El objetivo de este estudio es evaluar la relación entre la divergencia evolutiva y la conectividad histórica durante el Pleistoceno, integrando la modelación paleoclimática con el complejo de frailejones (subtribu Espeletiinae) como modelo biológico.

##### 

**Nota**: *Los títulos de las secciones metodológicas clave incluyen enlaces que dirigen a repositorios de GitHub con los códigos utilizados y explicaciones más detalladas de cada sección. Para revisar el proceso completo de este estudio, excluyendo la reconstrucción filogenética, consulta el siguiente [enlace.](https://innerhaze.github.io/Evolutionary-Divergence-Historical-Connectivity-in-Northern-Andean-Paramos-Pleistocene-/)*

------------------------------------------------------------------------

# **2. Metodología**

------------------------------------------------------------------------

### **2.1 Modelos de Conectividad Geográfica**

El estudio comenzó con el desarrollo de modelos de conectividad geográfica, basados en el modelo paleoclimático propuesto por Flantua et al. (2019). Este modelo describe las fluctuaciones del Límite Superior del Bosque (LSB) a lo largo de ≈2 millones de años, lo que permite evaluar cómo estos cambios afectaron la conectividad entre los fragmentos de páramo en los Andes.

1.  <div>

    > [**Desarrollo de la Matriz de Costos de Movimiento:**](https://github.com/innerhaze/DEM-Reclassification-R-Paramo-Connectivity-Modeling) Se construyó un raster de costos utilizando un Modelo Digital de Elevación (DEM) que abarca todas las áreas de páramo en los Andes del norte. Se asignaron costos específicos de movimiento a diferentes franjas altitudinales, reflejando la limitada capacidad de dispersión de los organismos de páramo. El costo de movimiento aumenta gradualmente a medida que se aleja del núcleo del páramo, reflejando las dificultades que enfrentan las especies para dispersarse entre fragmentos aislados.

    </div>

2.  <div>

    > [**Cálculo de Métricas de Conectividad:**](https://github.com/innerhaze/Java-R-Integration-with-Graphab-Cost-Surface-Processing-and-Data-Management) Utilizando el software Graphab, se calcularon diversas métricas de conectividad, incluidas la Distancia de Menor Costo (RMC) y el índice de Flujo de Corriente (CF). Estas métricas se determinaron para 19 configuraciones distintas de páramo, derivadas de las fluctuaciones climáticas del Pleistoceno, según el modelo de Flantua et al. (2019). Estos cálculos son fundamentales para entender cómo las fluctuaciones climáticas influyeron en la conectividad entre los parches que representan la distribución de cada una de las especies incluidas en la filogenia de Espeletiinae desarrollada por Diazgranados y Barber (2017).

    </div>

------------------------------------------------------------------------

### **2.2 Métodos Filogenéticos**

Con los modelos de conectividad ya establecidos, se procedió a la construcción de una filogenia ultramétrica de Espeletiinae. Se utilizaron datos de secuencias de ADN de los genes ETS, ITS, y rpl16, obtenidos de estudios previos realizados por Diazgranados y Barber (2017). Estas secuencias se concatenaron y se utilizó el software IQ-TREE para construir la filogenia basada en el modelo GTR+I+G. La calibración del árbol se realizó considerando eventos históricos clave, como la divergencia entre clados de Espeletiinae en Venezuela y Colombia, situando la corona del árbol en aproximadamente 2.3 millones de años, siguiendo la metodología de Pouchon et al. (2021).

------------------------------------------------------------------------

### **2.3 Empleo del Algoritmo de Conectividad Histórica**

Se utilizó un algoritmo desarrollado en R para integrar la información de los modelos de conectividad y la filogenia. Este algoritmo pondera las métricas de conectividad en función de la duración de cada configuración de páramo durante el intervalo de tiempo entre los nodos padre e hijo en la filogenia. Este intervalo se selecciona para representar el período en el que, hipotéticamente, las fluctuaciones climáticas del Pleistoceno habrían influido en la conectividad, aumentando o disminuyendo el aislamiento entre especies. Una vez establecidos estos tiempos clave, el algoritmo consulta la base de datos del modelo paleoclimático de Flantua et al. (2019) para obtener las configuraciones de páramo y su duración durante esos intervalos. Con esta información, calcula una media ponderada que refleja la conectividad histórica para cada par de combinaciones filogenéticas, asegurando que los períodos críticos de divergencia entre especies se consideren adecuadamente en el análisis, siempre que estos tiempos no superen los 2.2 millones de años, que es el intervalo cubierto por el modelo paleoclimático. Visita el siguiente [enlace](https://github.com/innerhaze/R-Algorithm-for-Historical-Connectivity-Analysis-of-Paramo-Lineages-in-the-Pleistocene) para mas detalles.

------------------------------------------------------------------------

### **2.4 Modelo de Disimilitud Generalizada (GDM)**

Después de generar los datos de conectividad histórica a partir del algoritmo diseñado, se empleó un Modelo de Disimilitud Generalizada (GDM) para evaluar la relación entre la conectividad histórica y la divergencia evolutiva en Espeletiinae. El GDM permitió analizar cómo las métricas de conectividad histórica, calculadas en función de las configuraciones de páramo durante el Pleistoceno, se correlacionan con las distancias evolutivas entre los linajes. Visita el siguiente [enlace](https://github.com/innerhaze/Generalized-Dissimilarity-Modeling-for-Evolutionary-Divergence-and-Historical-Connectivity-Analysis) para mas detalles.

------------------------------------------------------------------------

# **3. Resultados Principales**

Los resultados indican que la conectividad geográfica durante el Pleistoceno tuvo un impacto significativo en la divergencia evolutiva de Espeletiinae. En particular, la conectividad histórica emergió como una variable explicativa clave de las distancias evolutivas cuando los parches (sitios de ocurrencia) estaban más alejados entre sí. En contraste, cuando los parches se encontraban más cercanos, la distancia euclidiana resultó ser un factor más determinante.

------------------------------------------------------------------------

# **4. Problemas y Retos Metodológicos**

A continuación, se presentan algunos problemas y retos a abordar dentro de los aspectos metodológicos:

1.  <div>

    > **Temporalidad de los datos de ocurrencia:** La ocurrencia de cada linaje en el paisaje se basa en datos actuales. Por lo tanto, los cálculos de conectividad se realizan sobre la base de la distribución presente, ya que no se dispone de información precisa sobre la ubicación histórica de estos organismos. Esto se ilustra claramente en la figura 2 de este [enlace](https://innerhaze.github.io/R-Algorithm-for-Historical-Connectivity-Analysis-of-Paramo-Lineages-in-the-Pleistocene/)

    </div>

2.  <div>

    > **Complejidad en la medición de conectividad:** Cuando las especies ocurren dentro del mismo parche, se complica la medición de la conectividad en Graphab. Esto se debe a que dos o más especies, cuando se encuentran en puntos adyacentes de ocurrencia, son tratadas como una única unidad de parche, lo que dificulta las mediciones que estan pensadas para realizarse entre pares de especies.

    </div>

3.  <div>

    > **Limitaciones temporales en estudios filogenéticos:** Las filogenias estudiadas con este método no pueden exceder los 2.2 millones de años en sus tiempos de estudio, ya que este es el rango máximo de datos disponibles en la columna de polen utilizada.

    </div>

------------------------------------------------------------------------

# **5. Referencias**

1.  Diazgranados, M., & Barber, J. C. (2017). The endemic Espeletia complex: Phylogenetics, morphological evolution, and biogeography of the most diverse plant clade in the high Andes. Frontiers in Plant Science, 8, 2058.
2.  Pouchon, C., et al. (2021). Phylogenetic signatures of ecological divergence and leapfrog adaptive radiation in Espeletia. American Journal of Botany, 108(1), 113-128.
3.  Flantua, S. G. A., O'Dea, A., Onstein, R. E., Hooghiemstra, H., & Hoorn, C. (2019). The flickering connectivity system of the north Andean páramos. Journal of Biogeography, 46(8), 1808-1825.
