---
titulo: Minería de Datos – 05. Evaluación de modelos
serie: Minería de Datos – Introducción
playlist: https://www.youtube.com/playlist?list=PLrc3rKEj3Qc9DCowe-5CIWmYlngJLLOw8
tipo: Apuntes introductorios
nivel: Introductorio
---
### 1. Clasificación Bayesiana y el Supuesto de Independencia

La clasificación Bayesiana es teóricamente un muy buen método que proporcionaría el mejor resultado posible si se pudieran almacenar todas las dependencias condicionales de las variables.

**Problemas de No Independencia:** Si no se asume independencia, surgen dos problemas principales que impiden el uso directo de las probabilidades completas $P(X | H)$:
1.  **Imposibilidad de Almacenamiento:** No se pueden almacenar todas las combinaciones. El número de tuplas a almacenar sería exponencial (por ejemplo, $2^K$ para $K$ atributos con dos posibilidades cada uno).
2.  **Falta de Datos de Entrenamiento:** No se ha visto suficiente data para cubrir todas las combinaciones. Si llega un nuevo punto de datos con una combinación no vista, la probabilidad de ver esa combinación es cero, lo que impide predecir cualquier cosa.

**El Supuesto de Independencia:**
Estos problemas llevan a la necesidad de asumir la **independencia** de los atributos. Esto significa asumir que cada atributo es independiente de los demás (aunque en la práctica esto puede no ser cierto, como la edad y los ingresos).
Si se asume la independencia, la probabilidad condicional del vector de atributos $P(X_1, ..., X_M | C_J)$ se puede calcular multiplicando las probabilidades de cada atributo por separado: $\prod P(X_i | C_J)$.

**Ventajas del Clasificador Naive Bayes:**
Es fácil de implementar, muy rápido en el tiempo de predicción (ya que muchas probabilidades se pueden calcular previamente y solo se requiere multiplicar), y las actualizaciones con nuevos datos son sencillas.

**El Problema del Cero (Zero Stability):**
A pesar del supuesto de independencia, el producto de probabilidades puede dar cero si solo una de las probabilidades individuales es cero (es decir, si esa instancia particular del atributo nunca se ha visto en esa clase).
La solución práctica es añadir un pequeño **pseudo-conteo** (como $+1$) a los números para evitar que la probabilidad sea cero, lo que no afecta significativamente los cálculos en grandes conjuntos de datos.

### 2. Redes Bayesianas (Bayesian Networks)

Cuando existen **dependencias fuertes** que no pueden ignorarse (como en el diagnóstico médico, donde el cáncer de pulmón depende del historial familiar y de si se es fumador), la clasificación Naive Bayes podría ser incorrecta.
Las redes Bayesianas permiten **modelar explícitamente solo las dependencias más importantes**. Esto requiere definir tablas de probabilidades condicionales para cada relación de dependencia.
Aunque las redes Bayesianas son un método competitivo y pueden ofrecer mejor precisión al modelar dependencias, su gran desventaja es que se necesita **modelar explícitamente las redes** y tener una gran cantidad de datos de entrenamiento para completar todas las tablas de estadísticas necesarias.

### 3. Límites de Decisión y Máquinas de Vectores de Soporte (SVM)

La clase pasó a examinar los **límites de decisión**, simplificando a dos clases y dos dimensiones, aunque en dimensiones superiores el límite lineal se convierte en un **hiperplano**.

**El Límite de Decisión Ideal:**
El límite ideal no solo debe separar las dos clases, sino que debe **maximizar el margen** (la distancia al punto más cercano de cada clase).

**Formulación Matemática de SVM:**
Las SVM están diseñadas para encontrar el hiperplano que maximice este margen.
El objetivo de optimización, que es maximizar el margen $2/||W||$, es matemáticamente equivalente a **minimizar $1/2$ por la norma al cuadrado del vector $W$**.
Esta es una **optimización restringida**. Los puntos de datos actúan como restricciones que aseguran que todos los puntos estén en el lado correcto del hiperplano.
La solución se encuentra usando la **formulación de Lagrange**, resolviendo para los coeficientes $\alpha_i$. Los puntos de datos asociados a un $\alpha_i$ positivo son los **vectores de soporte**, que son los que definen el margen.

**Solución a la Separabilidad No Lineal:**
Las SVM enfrentan problemas si los datos no son linealmente separables o si hay ruido que impide la partición perfecta.
1.  **Márgenes Suaves (Soft Margins):** Permiten algunas violaciones a las restricciones (permitiendo que algunos puntos estén en el lado incorrecto) para encontrar la mejor separación posible en datos con ruido.
2.  **Funciones Kernel:** Transforman los datos originales, que no son linealmente separables (ej. círculos concéntricos), a un **espacio de dimensión superior** donde sí pueden separarse linealmente mediante un hiperplano.
    *   La clave es que la regla de decisión y la maximización solo requieren el cálculo del **producto punto** de los datos. Si se puede calcular el kernel (el producto punto transformado) sin mapear explícitamente los datos al nuevo espacio, se simplifica la computación.
    *   Los kernels más comunes son los **Polinomiales** y los **Gaussianos** (RBF).
    *   La idea del kernel (aprender una transformación para que las tareas posteriores sean resolubles) es fundamental en machine learning.

**Resumen de SVM:**
Las SVM tienen una **fuerte base matemática**, encuentran un óptimo global y escalan bien a conjuntos de datos de alta dimensión. Sin embargo, son **ineficientes en la construcción del modelo** (tiempos de entrenamiento largos) y el **modelo es difícil de interpretar**; no se puede explicar fácilmente por qué una clasificación es positiva o negativa.

### 4. Evaluación de Clasificadores

**Validación Cruzada N-fold:**
Se debe particionar el conjunto de datos en **entrenamiento, validación** (usado por el modelo para optimizar, ej., evitar el sobreajuste) y **prueba** (usado para la evaluación final y nunca visto por el modelo).
La validación cruzada $N$-fold divide los datos en $N$ partes (o *folds*). Se usa $N-1$ para entrenamiento y una para validación, rotando el fold de validación $N$ veces para construir $N$ modelos. Esto se hace para **evitar un mal split inicial**. $N=10$ es un método común.

**Métricas de Evaluación:**
*   **Exactitud (Accuracy):** El porcentaje de objetos del conjunto de prueba donde la clase predicha es igual a la clase real.
*   **Tasa de Error (Error Rate):** El inverso de la exactitud (predicción desigual a la clase real).
*   **Precisión (Precision):** Ítems relevantes recuperados divididos por el número total de ítems recuperados.
*   **Exhaustividad o Recuperación (Recall):** Ítems relevantes recuperados divididos por todos los ítems relevantes disponibles. Mide cuántos ítems relevantes se perdieron.
*   **Medida F (F-Measure):** Una combinación de precisión y exhaustividad (2 * P * R / (P + R)).

**Curvas ROC (Receiver Operating Characteristics):**
Las curvas ROC trazan la **Tasa de Verdaderos Positivos** contra la **Tasa de Falsos Positivos**. Se desea que la curva vaya hacia la esquina superior izquierda (alta tasa de verdaderos positivos, baja tasa de falsos positivos). Son apropiadas cuando las observaciones están **balanceadas** entre las clases.
