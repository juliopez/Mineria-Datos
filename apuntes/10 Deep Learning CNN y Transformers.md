---
titulo: Minería de Datos – 08. Deep Learning CNN y Transformers
serie: Minería de Datos – Introducción
playlist: https://www.youtube.com/playlist?list=PLrc3rKEj3Qc9DCowe-5CIWmYlngJLLOw8
tipo: Apuntes introductorios
nivel: Introductorio
---
### I. Arquitectura y Fundamentos: El Perceptrón Multicapa (MLP)

El modelo base es el Perceptrón Multicapa (MLP). Una red neuronal se compone de capas que procesan la información de manera secuencial.

1.  **Estructura del MLP:** Consiste en una **capa de entrada** (que recibe las variables $x$), una o más **capas ocultas** (que transforman la información), y una **capa de salida** (que entrega la predicción final).
2.  **Profundidad vs. Ancho:** Se puede hacer una red más **ancha** (más neuronas por capa) o más **profunda** (más capas ocultas). La **profundidad** es esencial porque permite a la red aprender **representaciones jerárquicas** y resolver problemas complejos.
3.  **Funciones de Activación:** Cada neurona aplica una transformación lineal ($z = w\cdot x + b$) seguida de una función de activación. Es crucial que estas funciones sean **NO lineales**, ya que una red compuesta solo por transformaciones lineales colapsaría en una única transformación lineal, perdiendo la capacidad de aprender patrones complejos.
    *   Las activaciones comunes incluyen **ReLU** (la más utilizada en redes modernas por su simplicidad y eficiencia), **Leaky ReLU** (para evitar "neuronas muertas"), **Sigmoide** (usada en clasificación binaria, aunque puede saturarse), y **Tanh**. Las diferencias entre ellas son principalmente prácticas (velocidad y estabilidad).

### II. Proceso de Entrenamiento y Backpropagation

El entrenamiento de una red neuronal es un proceso de optimización que utiliza el **descenso de gradiente**, aprovechando que las redes son modelos **diferenciables**.

1.  **Forward Pass (Paso Adelante):** Los datos de entrada pasan por todas las capas de la red para generar una predicción de salida.
2.  **Cálculo del Error (Loss):** La predicción ($\hat{y}$) se compara con el valor real ($y$) utilizando una función de pérdida (ej. MSE para regresión o *Cross-entropy* para clasificación).
3.  **Backpropagation (Propagación hacia Atrás):** Este es el algoritmo central del aprendizaje. El error se **propaga hacia atrás** desde la capa de salida a través de todas las capas. Mediante el cálculo de derivadas parciales (gradientes) se determina **cuánto y en qué dirección** debe ajustarse cada peso de la red.
4.  **Proceso Iterativo:** El entrenamiento es repetitivo. Con cada iteración (o *epoch*), la pérdida disminuye, lo que se observa en la **curva de aprendizaje**, indicando convergencia.

### III. Decisiones Prácticas y Pipeline Completo

Para implementar y entrenar una red neuronal con éxito, se sigue un *pipeline* que incluye decisiones clave:

1.  **Preparación de Datos:** Es fundamental que las entradas sean **vectores de números**. Esto requiere normalizar las entradas para mejorar la estabilidad de los gradientes, y codificar variables categóricas, por ejemplo, mediante *one-hot encoding*.
2.  **Inicialización de Pesos:** Una buena inicialización acelera el aprendizaje y previene problemas de gradientes. El uso de cero debe evitarse. Se recomiendan estrategias como **He** (ideal para activaciones ReLU) o **Xavier** (ideal para Tanh).
3.  **Definición de Arquitectura:** No existen reglas fijas para elegir el número de capas o neuronas. La arquitectura se define basándose en la **experiencia**, el **ajuste de hiperparámetros** (como *grid search*) y la revisión de **benchmarks** existentes.
4.  **Benchmarks (ImageNet):** El historial de ImageNet demuestra que el diseño arquitectónico (ej. AlexNet, ResNet) sí es crucial para reducir significativamente el error en problemas complejos, un conocimiento que se adquiere experimentalmente.
