---
titulo: Minería de Datos – 03. Preprocesamiento y calidad de datos
serie: Minería de Datos – Introducción
playlist: https://www.youtube.com/playlist?list=PLrc3rKEj3Qc9DCowe-5CIWmYlngJLLOw8
tipo: Apuntes introductorios
nivel: Introductorio
---
### 1. Regresión (Regression)

La regresión es el proceso de **ajustar una función a los datos** con el objetivo de revelar patrones, tendencias o la estructura subyacente. En el contexto de la limpieza de datos, se utiliza para suavizar la información y manejar el ruido inherente a las mediciones de la vida real.

*   **Regresión Lineal:** Implica ajustar una línea recta a través de puntos de datos. El objetivo es **elegir los parámetros** (la pendiente $a$ y la intersección $b$ con el eje Y) de manera que el error sea lo más pequeño posible.
*   **Método de Mínimos Cuadrados (Least Squares):** El error se minimiza utilizando el método de los mínimos cuadrados (o error cuadrático medio), donde se busca que **la suma de los errores al cuadrado sea mínima**.
*   **Outliers (Valores atípicos):** Un punto de datos muy alejado (outlier) puede **perturbar y sesgar significativamente** la aproximación de la curva. El manejo de valores atípicos es crucial en la ciencia de datos.
*   **Regresión No Lineal:** Se utiliza cuando la señal de medición subyacente **no es lineal**. Los tipos comunes incluyen funciones polinomiales (de tercer grado, cuarto grado, etc.), exponenciales o logarítmicas.

### 2. Manejo de Ruido y Agrupamiento (Clustering)

El agrupamiento (clustering) ayuda a identificar **grupos y valores atípicos**.

*   **Propósito:** Se utiliza para **detectar regiones de ruido** o puntos de datos ruidosos, especialmente en datos 2D, antes de entrenar un modelo.
*   **Algoritmos Comunes:** Incluyen K-means (que identifica centros de clústeres tomando el promedio de los valores) y DBScan (que puede detectar regiones de ruido de forma natural).

### 3. Datos Inconsistentes y Calidad de Datos

Los datos inconsistentes son aquellos que no tienen sentido lógico o semántico, son incompatibles o les faltan valores.

*   **Tipos de Inconsistencia:** Incluyen formatos de fecha diferentes, variaciones de ortografía, uso inconsistente de mayúsculas/minúsculas o problemas estructurales (p. ej., una columna de ubicación que luego se desglosa en calle, número, etc.).
*   **Solución:** No existe una única "corrección" correcta, ya que la solución a menudo **depende del dominio** y requiere intuición humana (por ejemplo, una edad de 150 años puede ser un error humano o ser real si se trata de una ballena).

### 4. Normalización y Estandarización

Ambas técnicas son importantes, especialmente para ejecutar modelos de *machine learning*.

*   **Propósito General:** Evitar que características con rangos muy grandes (como los ingresos) eclipsen o "ensombrezcan" a características con rangos pequeños (como la edad) durante el análisis o la visualización.
*   **Normalización (Min-Max):**
    *   Fija un rango predefinido (generalmente 0 a 1).
    *   Mantiene las diferencias relativas.
    *   La fórmula es: $X' = (X - \text{Mínimo}) / (\text{Máximo} - \text{Mínimo})$.
    *   Se pueden usar transformaciones no lineales como la **raíz cuadrada** o el **logaritmo natural** (normalización logarítmica) para hacer más obvios los datos, dependiendo del problema.
*   **Estandarización (Standardization):**
    *   Busca que la distribución de los datos tenga una **media de cero y una desviación estándar de uno**.
    *   Esto es crucial porque muchos algoritmos (como los métodos de descenso de gradiente) funcionan mejor o asumen distribuciones casi normales.
    *   Implica restar la media y dividir por la desviación estándar.

### 5. Muestreo (Sampling)

El muestreo se utiliza para seleccionar un subconjunto de datos.

*   **Motivación:** Reducir costos computacionales, hacer que grandes conjuntos de datos sean manejables y permitir un procesamiento más rápido.
*   **Requisito Clave:** La muestra debe estar **bien elegida** y ser **representativa** de los datos completos para capturar todas las variaciones relevantes.
*   **Tipos de Muestreo Probabilístico:**
    1.  **Muestreo Aleatorio Simple:** Cada punto tiene la misma probabilidad de ser seleccionado. Es fácil, pero puede resultar en muestras desequilibradas.
    2.  **Muestreo Sistemático:** Se selecciona cada K-ésimo punto después de ordenar los datos.
    3.  **Muestreo Estratificado:** Los datos se dividen en subgrupos (estratos) basados en una característica común y se muestrea aleatoriamente desde cada estrato (proporcional o equitativamente). Es útil cuando los subgrupos difieren significativamente.
    4.  **Muestreo por Conglomerados (Cluster):** Se seleccionan clústeres (grupos, a menudo basados en ubicación) basados en propiedades.

### 6. Remuestreo e Interpolación

Se usan para estimar valores desconocidos o faltantes.

*   **Interpolación:** Estima valores **entre** los puntos de datos conocidos. A diferencia de la regresión, la línea de interpolación debe **pasar por los puntos de datos** (no se asume ruido) y se utiliza para reconstruir una representación continua o generar una señal más suave.
    *   Ejemplos incluyen la interpolación lineal y la interpolación polinomial.
*   **Diferencia clave con la Regresión:** La **regresión** encuentra una función que se ajusta mejor a la tendencia *general* (con un error asociado y asumiendo ruido), mientras que la **interpolación** estima valores *intermedios* asumiendo que los puntos de datos iniciales son precisos y confiables.

### 7. Reducción de Dimensionalidad

Se trata de reducir un espacio de datos de alta dimensión a una dimensión baja.

*   **Objetivo:** Mantener la estructura intrínseca y la variación de los datos de alta dimensión tanto como sea posible.
*   **Beneficios:** Mejora la eficiencia computacional, ayuda a la visualización (por ejemplo, mostrando clústeres) y reduce la redundancia.
*   **Ejemplo:** El Análisis de Componentes Principales (PCA), que captura la varianza de los datos al rotar el sistema de ejes hacia la dirección del cambio más grande.



