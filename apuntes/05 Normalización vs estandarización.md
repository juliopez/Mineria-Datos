---
titulo: Minería de Datos – 05. Normalización vs estandarización
serie: Minería de Datos – Introducción
playlist: https://www.youtube.com/playlist?list=PLrc3rKEj3Qc9DCowe-5CIWmYlngJLLOw8
tipo: Apuntes introductorios
nivel: Introductorio
---

La **normalización** y la **estandarización** son procesos críticos de transformación de datos que aseguran que las diferentes características de un conjunto de datos sean comparables entre sí, evitando que atributos con escalas grandes dominen injustamente el modelo.

### Normalización
La normalización se utiliza principalmente cuando las características tienen rangos de valores muy dispares.
*   **Propósito:** Evitar que características de gran escala (como el ingreso anual de 100,000) eclipsen a características de escala pequeña (como la edad de 25), ya que muchos algoritmos asumen que todas las distancias tienen el mismo peso.
*   **Método Min-Max:** Es la técnica más común y consiste en **mapear los valores a un rango fijo, generalmente entre 0 y 1**.
*   **Cálculo:** Se resta el valor mínimo del atributo a cada dato y se divide por el rango total (máximo menos mínimo).
*   **Ventajas:** Preserva las distancias relativas entre los datos y ayuda a comprimir el impacto de los valores atípicos (*outliers*).
*   **Variantes:** Para datos con valores muy extremos, se pueden emplear la normalización por **raíz cuadrada** o el **logaritmo natural**, que ayudan a visualizar mejor las distribuciones sesgadas.

### Estandarización
La estandarización (también conocida como normalización Z-score) transforma los datos basándose en sus propiedades estadísticas.
*   **Propósito:** Hacer que las características sean directamente comparables desde una perspectiva de aprendizaje automático, alineando atributos que tienen diferentes escalas en una distribución común.
*   **Objetivo:** Lograr que los datos tengan una **media de cero y una desviación estándar de uno**.
*   **Cálculo:** Primero se resta la media del atributo a cada valor para centrarlo en cero y luego se divide por la desviación estándar para ajustar la escala.
*   **Importancia en Deep Learning:** Es vital para modelos que utilizan el **descenso de gradiente**, ya que estos algoritmos son muy sensibles a datos que no siguen una distribución estándar, lo que podría desestabilizar el aprendizaje.

### Diferencias Clave
| Característica | Normalización | Estandarización |
| :--- | :--- | :--- |
| **Rango de salida** | Generalmente **fijo (0 a 1)**. | Sin rango fijo; centrado en **media 0**. |
| **Distribución** | Mantiene la forma original pero cambia la escala. | Transforma los datos hacia una **distribución normal**. |
| **Uso principal** | Cuando se requiere un rango acotado o para visualización. | Para algoritmos sensibles a la magnitud como el **descenso de gradiente**. |

**Analogía:** Imagina que quieres comparar el rendimiento de dos estudiantes: uno tomó un examen de 10 preguntas y otro uno de 100. La **normalización** sería como convertir ambas calificaciones a un porcentaje del 0 al 100%. La **estandarización** sería como analizar qué tan lejos está cada estudiante del promedio de su propio salón; así podrías saber quién es más "sobresaliente" independientemente de cuántas preguntas tenía su examen.

---

> La elección entre normalización y estandarización depende del algoritmo utilizado y de la distribución de los datos, ya que no todos los modelos son igualmente sensibles a la escala.
