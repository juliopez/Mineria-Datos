---
titulo: Minería de Datos – 09. Arquitecturas Deep Learning
serie: Minería de Datos – Introducción
playlist: https://www.youtube.com/playlist?list=PLrc3rKEj3Qc9DCowe-5CIWmYlngJLLOw8
tipo: Apuntes introductorios
nivel: Introductorio
---
### Optimización y Entrenamiento

El entrenamiento de redes neuronales utiliza el Descenso de Gradiente Estocástico (**SGD**), que calcula los gradientes en submuestras de los datos (*minibatches*) en lugar de en el conjunto de datos completo, lo cual es más eficiente.

Para mejorar el Descenso de Gradiente "Vanilla", que puede estancarse en mesetas o tener gradientes muy bajos, se utiliza la técnica de **Momentum**. La idea del *momentum* es **mantener el impulso** del paso anterior para que la actualización del peso no dependa únicamente del gradiente local actual. Esto permite continuar rodando hacia el mínimo incluso en áreas planas. Otros optimizadores, como NAG, Adagrad, Adadelta y RMSprop, también buscan converger más rápido que el SGD.

### Regularización

La **Regularización** es un requisito clave para evitar el **sobreajuste (overfitting)**, que ocurre cuando las redes profundas se ajustan a funciones demasiado complejas, logrando una alta precisión en el entrenamiento pero baja generalización en datos nuevos.

La regularización **penaliza la complejidad** de la red.

*   **Norma L2 (L2-regularization):** Es la forma más común. Se añade un término a la función de pérdida (loss function) que es proporcional a la suma de los cuadrados de todos los pesos ($\Sigma ||\theta||^2$), lo que evita que los pesos individuales se vuelvan excesivamente grandes. Esto aumenta artificialmente la pérdida y obliga a que los pesos permanezcan en un rango acotado.
*   **Dropout:** Una técnica popular donde se ignoran algunos nodos (estableciendo su valor a cero) durante el entrenamiento, mejorando la eficiencia y efectividad.

### Clasificación y Arquitectura Básica

Para tareas de **clasificación no binaria**, se utilizan múltiples salidas de la red neuronal, donde cada salida representa la predicción para una clase específica.

Para convertir estas salidas numéricas en **probabilidades** que sumen 1, se aplica la función de activación **Softmax**. Por ejemplo, en un caso de clasificación de dígitos, Softmax convierte los valores pre-Softmax en probabilidades claras, resultando en una probabilidad cercana al 100% para el dígito correcto una vez que la red está entrenada.

El avance del **Deep Learning** se debe en gran medida a la capacidad de escalar las redes neuronales utilizando **GPUs** (Unidades de Procesamiento Gráfico), que pueden computar miles de multiplicaciones de matrices en paralelo, lo que es esencial para el funcionamiento interno de las neuronas.

### Deep Learning y Bias Inductivo

La intuición del *Deep Learning* se basa en que, aunque una red superficial de dos capas (MLP) podría representar cualquier función (Teorema de Aproximación Universal), requeriría un número exponencial de nodos y pesos, lo que lleva a la memorización y mala generalización.

Las **redes profundas** (más capas) modelan funciones complejas de manera más compacta y con menos parámetros, permitiendo una mejor generalización (mayor precisión de prueba).

El **Aprendizaje de Representaciones (Representation Learning)** es clave: la red multicapa aprende una transformación de los datos de entrada a un espacio latente adecuado. El proceso fundamental del *Deep Learning* consiste en la Codificación de Entrada (Input Encoding) + Aprendizaje de Representación Latente + Función de Pérdida Específica de la Tarea.

El **Bias Inductivo** es el conjunto de suposiciones utilizadas sobre la estructura de los datos para elegir una arquitectura de red especializada. Por ejemplo, para datos de imagen se usa la suposición de **Localidad**, mientras que para datos de texto se requiere **Secuencialidad**.

### Arquitecturas Especializadas

#### Redes Neuronales Convolucionales (CNNs)
Las MLPs no son adecuadas para imágenes grandes porque aplanarlas resulta en una cantidad masiva y prohibitiva de pesos (cientos de millones).

Las **CNNs** utilizan **kernels convolucionales** como bloques de construcción.

*   **Conectividad Local y Peso Compartido:** A diferencia de una MLP totalmente conectada, en una CNN, cada neurona solo se conecta a una pequeña región local de la entrada, y el mismo conjunto de pesos (*kernel*) se aplica a todas las áreas.
*   **Convolución y Submuestreo (Downsampling):** La operación de convolución es esencialmente una multiplicación de matrices entre el *kernel* de pesos y una sección de la imagen. La red jerárquica de CNNs apila múltiples capas donde se alterna la convolución y el **submuestreo**.
*   **Downsampling (Pooling & Striding):** El submuestreo reduce la resolución espacial y aumenta el campo receptivo. **Pooling** (típicamente *max pooling*) combina los valores de múltiples píxeles en uno solo, tomando el valor máximo.
*   La ventaja de la jerarquía de capas es que permite a la red aprender características con **diferentes niveles de resolución**, desde características de bajo nivel (bordes) hasta características de alto nivel (partes de objetos).

#### Transformers (para Datos de Texto)
Los datos de texto son secuenciales y presentan difíciles **dependencias de largo alcance**. Las Redes Neuronales Recurrentes (RNNs) tenían problemas para modelar estas dependencias de largo alcance y eran difíciles de paralelizar.

El gran avance provino del mecanismo de **Auto-Atención (Self-Attention)**, cuya idea clave es que **cualquier *token* puede ser relevante para cualquier otro *token*** en la secuencia. Esto permite capturar dependencias de largo alcance y bidireccionales.

El **Transformer** es una arquitectura basada en la auto-atención, diseñada originalmente para la traducción.

Componentes clave del Transformer:
1.  **Tokenización y Embeddings Posicionales:** Las palabras se convierten en *tokens* numéricos. Los **Embeddings** convierten los *tokens* en vectores. Se añade la **Codificación Posicional** porque, por defecto, la capa de auto-atención no tiene concepto de secuencia u orden.
2.  **Arquitectura Encoder-Decoder:** Consiste en un *Encoder* (que convierte el texto en *embeddings* latentes) y un *Decoder* (que genera la salida, basándose en los *embeddings* más la traducción ya generada).
3.  **Bloques de Atención:** La matriz de entrada se convierte en tres matrices aprendibles: **Query (Consulta)**, **Key (Clave)** y **Value (Valor)**, que se utilizan para calcular la auto-atención.
4.  **Atención Multi-Cabeza (Multi-Head Attention):** Se utilizan múltiples "cabezas" de atención para permitir que la red aprenda diferentes patrones de atención o contextos distintos en paralelo.
