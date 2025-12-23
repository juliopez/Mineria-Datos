---
titulo: Minería de Datos – 02. Visualización y tipos de datos
serie: Minería de Datos – Introducción
playlist: https://www.youtube.com/playlist?list=PLrc3rKEj3Qc9DCowe-5CIWmYlngJLLOw8
tipo: Apuntes introductorios
nivel: Introductorio
---
### I. La Importancia de la Visualización

*   **Ventajas de la Visualización:** Se demostró que la forma visual permite retener y comprender mucha más información, como tendencias de subidas y bajadas, en comparación con mirar solo números, incluso dándoles más tiempo.
*   **Estadísticas vs. Visualización:** Se presentó un ejemplo de cuatro conjuntos de datos (A, B, C, D) que comparten las **mismas estadísticas de primer orden** (misma media de X y Y, misma correlación, misma línea de regresión), pero visualmente son sorprendentemente diferentes (desarrollo lineal, desarrollo lineal más sesgado, curva cuadrática).
*   **Poder de la Visualización:** La visualización permite juzgar inmediatamente las diferencias entre conjuntos de datos que son estadísticamente idénticos. Esto es crucial porque la estadística por sí sola no siempre ayuda a distinguir conjuntos de datos, especialmente si son datos artificiales diseñados para tener las mismas estadísticas pero formas muy diferentes (circular, aleatoria, etc.).

### II. El Proceso de Ciencia de Datos y Minería

El tiempo dedicado a las diferentes partes del proceso de minería de datos, señalando que el aprendizaje automático (Machine Learning, ML) es solo una pequeña porción del contexto más amplio, a menudo llamado Ciencia de Datos o Minería de Datos.

*   **Distribución de Tiempo:** Aproximadamente el **80% del tiempo** se dedica a tareas que no son la ejecución real del modelo:
    *   Carga de datos: 20%.
    *   Limpieza de datos (Data Cleaning): 26%.
    *   Visualización de datos: 21%.
    *   Selección del modelo: 11%.
*   **Problemas de Datos:** Muchos problemas de datos son "silenciosos", como valores atípicos (outliers), duplicados, errores tipográficos (typos) y valores inexistentes. Si no se limpian los datos, el modelo no será útil ("junk in junk out").
*   **Estructura del Curso:** El plan de la clase cubre las bases de datos y el pre-procesamiento, la construcción de modelos (Input/Output), la clasificación (considerado el problema más sencillo), la evaluación, el descenso de gradiente (fundamental para el aprendizaje profundo), el clustering y la minería de reglas.

### III. Fundamentos de los Datos y Tipos Estadísticos

Dado que el algoritmo y la arquitectura del modelo dependen del tipo de datos (discreto frente a continuo), es esencial comprender la naturaleza de los datos.

Los tipos de datos estadísticos, que se centran en la escala de medición, a diferencia de los tipos de datos en informática que se centran en el almacenamiento (strings, integers). La pregunta clave es si las operaciones son **significativas** en el contexto de la aplicación.

1.  **Datos Nominales (Categóricos sin orden):**
    *   Valores sin orden o clasificación intrínseca (ej. color, género, ID único, compañías de automóviles).
    *   Operaciones significativas: **igual y no igual**.
    *   Una ordenación puede imponerse (ej. color por valor RGB), pero no es nominal si dicha ordenación no es *significativa* para la aplicación.
2.  **Datos Ordinales (Categóricos con orden):**
    *   Valores que pueden ser ordenados, pero las diferencias relativas entre ellos no son comparables o cuantificables de manera significativa (ej. situación ruidosa/tranquila, grados escolares, hábitos de fumar: regular, a veces, pesado).
    *   Operaciones significativas: igual, no igual, **menor o mayor**.
    *   El hecho de que los datos ordinales puedan ser mapeados a números (ej. 0, 1, 2, 3) no los convierte en numéricos; siguen siendo ordinales si las operaciones numéricas (como la media o la diferencia) no son significativas.
3.  **Datos Numéricos (Cuantitativos):**
    *   Valores en los que las operaciones numéricas (calcular diferencias, promedios, ratios) son significativas (ej. altura de edificios, edad, tiempo de carrera).

### IV. Estructuras y Tipos de Datos Complejos

Los datos rara vez son escalares (un solo valor); usualmente vienen en estructuras más complejas.

*   **Vector/Multivariante:** Múltiples atributos para una sola entidad (ej. género, edad, peso de una persona). Se enfoca en lo que se mide sobre cada muestra y típicamente forma una matriz 2D (datos tabulares).
    *   *Dato Multivariante* se refiere a múltiples variables, y el espacio de datos puede ser disperso (no todas las combinaciones de altura/peso existen).
    *   *Dato Multi-dimensional* se enfoca en cómo se organizan los datos, a menudo en una cuadrícula densa donde existe un valor (o podría existir) para cada punto (ej. temperatura por longitud y latitud).
*   **Tensor:** Estructura 3D o superior, a menudo utilizada para series de tiempo, donde múltiples valores se miden a lo largo del tiempo para una entidad.
*   **Gráficos/Redes:** Miden relaciones entre nodos, como conexiones sociales, interacciones o hipervínculos. Los gráficos pueden tener propiedades como ser ponderados (weighted), dirigidos (directed) o dinámicos.
*   **Jerárquicos:** Pueden ser jerarquías definidas (ej. redes de direcciones IP) o jerarquías artificiales construidas a partir de otros datos (ej. un árbol de expansión mínima construido a partir de un grafo).
*   **Geoespaciales (Geo Data):** Datos geográficos importantes que combinan coordenadas (latitud/longitud) con puntos, líneas y polígonos (ej. ubicación de ciudades, calles, áreas de uso de la tierra).

### V. Pre-procesamiento de Datos (Data Pre-processing)

El pre-procesamiento es un paso de preparación para el modelado, asegurando que los datos sean consistentes, completos y útiles. Los pasos incluyen la limpieza, la normalización y la estandarización.

#### 1. Manejo de Valores Faltantes (Missing Values)

Los valores faltantes ocurren por fallas de sensores, campos opcionales, pérdida de datos en la transmisión, o capacidades de almacenamiento limitadas.

*   **Enfoques para la imputación:**
    1.  **Descartar/Ignorar:** El método más fácil, pero puede introducir sesgos si se pierden proporcionalmente más datos de un tipo de persona.
    2.  **Llenar manualmente:** El enfoque más costoso (ej. llamar a la persona).
    3.  **Llenar con una constante:** Como un valor por defecto (-1). Se debe tener cuidado, ya que esta constante puede tener un papel especial en el algoritmo posterior y no debe usarse para calcular promedios.
    4.  **Llenar con la media o la mediana:** Esto no destruye la media, pero crea un pico artificial en la distribución del valor imputado.
    5.  **Predecir el valor (Imputación algorítmica):** El método más sofisticado, utilizando las correlaciones de otros atributos para predecir el valor faltante. Sin embargo, se debe tener cuidado de no "redescubrir" estas predicciones como correlaciones genuinas en los resultados posteriores del modelo, ya que son artefactos del proceso de limpieza.

#### 2. Manejo de Datos Ruidosos (Noisy Data)

Los datos ruidosos contienen errores aleatorios o valores atípicos que no reflejan los valores verdaderos.

*   **Técnicas:** Binning (agrupación), Regresión y Clustering.
*   **Binning (Agrupación):** Consiste en ordenar los datos y dividirlos en contenedores (bins).
    *   *Binning de Ancho Igual (Equal Width):* Los bins tienen el mismo rango de valores (ej. 0-5, 5-10). Un valor atípico muy alto puede hacer que el rango de este bin sea enorme, dejando los otros bins vacíos.
    *   *Binning de Profundidad Igual (Equal Depth):* Cada bin contiene el mismo número de elementos.
    *   **Reemplazo de Valores:** Los valores dentro de cada bin se reemplazan por la media, la mediana o los límites del bin. Se debe tener cuidado: la media puede verse fuertemente afectada por valores atípicos, mientras que la mediana es más robusta. El binning actúa como un suavizado para las fluctuaciones de la curva de datos.
