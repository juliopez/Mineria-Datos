---
titulo: Minería de Datos – 07. Descenso de gradiente
serie: Minería de Datos – Introducción
playlist: https://www.youtube.com/playlist?list=PLrc3rKEj3Qc9DCowe-5CIWmYlngJLLOw8
tipo: Apuntes introductorios
nivel: Introductorio
---
El Descenso de Gradiente es la tecnología básica sobre la que funciona todo el aprendizaje automático (machine learning).

### 1. Conceptos Introductorios y Regresión

*   **Regresión vs. Clasificación:** La **regresión** predice un **valor numérico** o continuo (por ejemplo, el salario o el valor máximo de un préstamo). La **clasificación**, en cambio, predice un atributo categórico (como "sí" o "no", o la clase a la que pertenece un elemento).
*   **Fundamento Numérico:** El machine learning, al requerir un control estricto sobre la dirección del progreso, se basa en aspectos numéricos.

### 2. Componentes Fundamentales del Machine Learning

Para el aprendizaje automático se necesitan tres componentes principales:

1.  **Conjunto de Datos de Entrenamiento (Training Data Set):** No existe el machine learning sin datos para entrenar.
2.  **Modelo:** Es la función o el conjunto de funciones que el sistema optimiza. Para poder usar el Descenso de Gradiente, el modelo debe ser **diferenciable**. Si no es diferenciable, no se puede determinar la dirección a seguir.
3.  **Algoritmo de Aprendizaje Iterativo:** Basado en el Descenso de Gradiente.

### 3. La Función de Pérdida y el Descenso de Gradiente

El objetivo del algoritmo de aprendizaje es **minimizar la función de pérdida (Loss Function)**. La función de pérdida mide el rendimiento del modelo; una pérdida baja equivale a un error bajo y, por lo tanto, a una predicción precisa.

*   **Parámetros del Modelo ($\theta$):** Estos parámetros controlan el comportamiento del modelo (en el caso de la regresión lineal simple, son A y B, o $\theta_1$ y $\theta_2$ en la nueva nomenclatura).
*   **Función de Pérdida en Regresión:** Para la regresión lineal, la función de pérdida estándar es el **Error Cuadrático Medio (Mean Square Error - MSE)**. La pérdida se calcula como la diferencia al cuadrado entre el valor real ($Y$) y el valor predicho ($\hat{Y}$), promediado sobre todos los puntos de datos de entrenamiento.

El Descenso de Gradiente funciona adaptando los parámetros del modelo en pasos pequeños y graduales, en la **dirección de un error más pequeño**.

#### Cálculo y Actualización del Gradiente

1.  **Medición del Error:** Se toma una muestra del conjunto de entrenamiento y se mide el error de predicción del modelo.
2.  **Cálculo del Gradiente:** Se calcula el gradiente, que es la primera derivada parcial de la función de pérdida con respecto a cada parámetro del modelo ($\theta_1, \theta_2, \dots$). La derivada indica la dirección para cambiar los parámetros y disminuir el error. Este cálculo requiere el uso de reglas de diferenciación (como la regla de la cadena, la regla de la potencia y la regla del término constante).
3.  **Actualización de Parámetros:** Los parámetros se actualizan en la **dirección inversa del gradiente** (por eso se llama "descenso"). La fórmula general es: $\theta_{\text{nueva}} = \theta_{\text{antigua}} - (\text{Tasa de Aprendizaje} \times \text{Gradiente})$.
4.  **Iteración:** El proceso se repite con el siguiente ejemplo y muchas veces (muchas rondas) hasta que el modelo alcanza un error muy bajo o los parámetros convergen.

#### La Tasa de Aprendizaje ($\eta$)

La **tasa de aprendizaje (learning rate)** es un parámetro clave que determina qué tan rápido se adaptan los parámetros y el tamaño del paso que se da hacia el óptimo. Generalmente es un valor mucho menor que uno, como 0.01.

Existe un compromiso (trade-off):

*   **Tasa alta:** Permite un aprendizaje más rápido, pero conlleva el riesgo de **saltarse (overshooting)** el mínimo, perdiendo precisión.
*   **Tasa baja:** Requiere muchos más pasos, pero alcanza el mínimo con mayor precisión.

### 4. La Escala del Deep Learning

Aunque este ejemplo utiliza solo dos parámetros ($\theta_1, \theta_2$), los modelos modernos de Deep Learning, como los que se usan actualmente, tienen **millones o incluso miles de millones de parámetros** (los modelos exitosos actuales alcanzan rangos de 8 mil millones).

Esta escala masiva requiere:

*   Una **gran cantidad de datos de entrenamiento** (trillones de documentos).
*   **Trillones de rondas de entrenamiento**, lo que puede llevar meses.
*   **Enorme poder computacional** (GPU), donde los costos eléctricos para una sola ronda de entrenamiento pueden ascender a varios millones de dólares.

Los modelos con una función de pérdida **convexa** son más fáciles de optimizar porque tienen un único mínimo global. Sin embargo, en el Deep Learning, muchas funciones de pérdida no son convexas, lo que hace que el Descenso de Gradiente sea, a menudo, el mejor enfoque disponible, aunque pueda terminar en un óptimo local.

### 5. Aplicación a la Clasificación (Regresión Logística)

El Descenso de Gradiente es versátil y no solo se aplica a la regresión lineal, sino también a **redes neuronales** y **modelos de lenguaje**.

Para aplicar el Descenso de Gradiente a problemas de **clasificación**, se utiliza la **Regresión Logística**. Esta técnica codifica la probabilidad de pertenecer a una clase como una probabilidad numérica.

*   Utiliza la **función sigmoide** (o función lógica inversa) para ajustar los datos.
*   La función sigmoide predice la probabilidad de pertenecer a una clase.
*   Se establece un límite de decisión (por ejemplo, 50%).
*   Se utiliza el Descenso de Gradiente para aproximar la función sigmoide y establecer el límite de decisión óptimo.

Este mismo principio se aplica cuando se usa una red neuronal para tareas de clasificación, donde se utiliza una función logística en algún punto para tomar la decisión de salida.

---
El Descenso de Gradiente es como intentar bajar una montaña en la niebla.

*   El objetivo es encontrar el valle más profundo (el mínimo global de la pérdida).
*   No puedes ver el valle entero, pero en tu posición actual puedes sentir la pendiente más pronunciada (el gradiente) que indica el camino más rápido hacia abajo.
*   La tasa de aprendizaje es el tamaño de tus pasos: si das pasos demasiado grandes (tasa alta), puedes saltar accidentalmente el valle y empezar a subir de nuevo (overshooting). Si das pasos pequeños (tasa baja), tardarás más, pero tendrás más certeza de alcanzar el fondo.
