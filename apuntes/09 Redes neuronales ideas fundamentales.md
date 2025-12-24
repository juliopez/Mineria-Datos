---
titulo: Minería de Datos – 07. Redes neuronales ideas fundamentales
serie: Minería de Datos – Introducción
playlist: https://www.youtube.com/playlist?list=PLrc3rKEj3Qc9DCowe-5CIWmYlngJLLOw8
tipo: Apuntes introductorios
nivel: Introductorio
---
### 1. Introducción a las Redes Neuronales y Conceptos Avanzados

Debemos pasar de modelos lineales a **modelos no lineales** altamente parametrizados, lo cual es posible con las redes neuronales. El uso de una mayor cantidad de parámetros—pasando de dos a millones o miles de millones—permite realizar muchas más tareas y obtener resultados mucho más complejos.

*   **Algoritmo Clave:** Es necesario discutir la **Retropropagación (Back Propagation)**, que es el método para calcular el gradiente y adaptar los pesos de la red.
*   **Modelos de Lenguaje:** Modelos actuales muy complejos, como GPT-2 o GPT-4, poseen miles de millones de parámetros y requieren enormes cantidades de datos y potencia computacional para su entrenamiento.
*   **Naturaleza Estadística:** Es crucial entender que estos modelos son fundamentalmente **modelos estadísticos**, entrenados con datos, y no toman decisiones deliberadas ni poseen inteligencia humana en el sentido estricto. Su rendimiento depende de los datos con los que fueron entrenados.

### 2. El Perceptrón y la Neurona Artificial

La unidad básica de la red neuronal es la **neurona artificial** o **Perceptrón**.

*   **Inspiración Biológica:** El nombre se inspira en el cerebro (nodos y conexiones), aunque los sistemas biológicos son mucho más complejos (conexiones químicas, eléctricas, etc.), y las redes actuales son entre 100 y 1,000 veces más pequeñas en términos de conexiones que el cerebro humano.
*   **Funcionamiento:** La neurona artificial replica el proceso biológico de combinar múltiples entradas.
    1.  Toma una **suma ponderada (weighted sum)** de las entradas.
    2.  Si esa suma ponderada supera un **umbral no lineal**, la neurona "dispara" o genera una salida. Este proceso de decisión se llama **función de activación**.
*   **Parámetros:** Los **pesos** ($W_1$ a $W_N$) son los parámetros del modelo que se ajustan.
*   **Bias (Sesgo):** Se añade un término de **sesgo** (bias) que es necesario para que el modelo pueda aprender funciones que no estén centradas en cero.
*   **Regresores Logísticos:** Una neurona artificial es esencialmente un **regresor logístico** que utiliza funciones de activación.

### 3. Funciones de Activación y Diferenciabilidad

Para poder optimizar las redes neuronales utilizando el Descenso de Gradiente, la **función de activación debe ser diferenciable**.

*   Funciones escalonadas (step functions) no son diferenciables y, por lo tanto, no se utilizan en las redes neuronales.
*   Una función comúnmente utilizada es la **función sigmoide** (vista en la regresión logística), que proporciona un límite de decisión no lineal y es diferenciable, permitiendo la adaptación de los pesos mediante Descenso de Gradiente.

### 4. Perceptrones Multicapa (MLP) y Deep Learning

La combinación de múltiples perceptrones en capas distintas es la base del Deep Learning.

*   **Capas:** Típicamente hay una **capa de entrada (input layer)**, **capas ocultas (hidden layers)** y una **capa de salida (output layer)**.
*   **Deep Learning:** Se denomina **Deep Learning** cuando se usan múltiples capas.
*   **Conexión Completa (Fully Connected):** Cuando cada entrada de una capa está conectada a cada neurona de la siguiente capa, se dice que la capa está completamente conectada. Sin embargo, la conexión completa generalmente hace que el número de pesos **explote** fácilmente si hay muchas capas y neuronas, por lo que a menudo se evita, excepto en ciertas porciones de la red o en las últimas capas.

### 5. Teorema de Aproximación Universal

Un perceptrón multicapa que utiliza una función de activación no lineal tiene la capacidad, en principio, de **aproximar funciones arbitrarias** (Universal Approximation Theorem). Esta capacidad, que hace que las redes neuronales sean tan flexibles, se cumple teóricamente si se dispone de un número infinito de neuronas o capas.

### 6. Poder Computacional y Entrenamiento Paralelo

La velocidad del entrenamiento depende de la capacidad de calcular los pesos y gradientes de manera paralela en todas las capas.

*   **GPUs y TPUs:** Las tarjetas gráficas (GPUs) y las unidades de procesamiento tensorial (TPUs) son esenciales para el entrenamiento. Originalmente diseñadas para el procesamiento paralelo de gráficos (como el sombreado de millones de píxeles), se han reconvertido en grandes máquinas de procesamiento paralelo. Esto permite que se realicen millones de cálculos de neuronas en paralelo, lo que hizo posible el entrenamiento de modelos masivos.

### 7. Conceptos

*   **Tasa de Aprendizaje Extrema:** Una tasa de aprendizaje muy alta puede provocar un **salto constante (flipping)** y que el modelo falle en converger o estabilizarse, resultando en pérdidas muy malas. Una tasa de aprendizaje muy pequeña, aunque precisa, hace que la aproximación sea extremadamente lenta.
*   **Activación Lineal:** Una función de activación lineal no puede resolver problemas que requieren límites de decisión no lineales.
*   **Ingeniería de Características:** Se puede ayudar al modelo a aprender más rápido añadiendo valores de entrada transformados (por ejemplo, $x_1^2$ o $x_1 \times x_2$), sin cambiar la arquitectura de la red.
