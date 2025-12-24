---
titulo: Minería de Datos – 04. Datos faltantes y valores atípicos
serie: Minería de Datos – Introducción
playlist: https://www.youtube.com/playlist?list=PLrc3rKEj3Qc9DCowe-5CIWmYlngJLLOw8
tipo: Apuntes introductorios
nivel: Introductorio
---

El manejo de datos faltantes y atípicos (outliers) es una parte fundamental de la **limpieza de datos**, una etapa que consume aproximadamente el **80% del tiempo** en proyectos de minería de datos. No existe una única solución "correcta", ya que la efectividad depende del contexto del problema y del dominio de los datos.

A continuación, se detallan las estrategias más efectivas según el tipo de problema:

### 1. Manejo de Datos Faltantes
Existen diversos enfoques, desde los más simples hasta los más sofisticados:

*   **Ignorar o eliminar registros:** Es la opción más sencilla, pero puede introducir **sesgos** si los datos no faltan de manera aleatoria (por ejemplo, si solo las personas mayores omiten su edad).
*   **Llenado manual:** Es el método más preciso pero también el más **costoso** en términos de tiempo y esfuerzo.
*   **Uso de constantes:** Se puede asignar un valor como "-1" para identificar el vacío, pero se debe tener cuidado de no incluir estos valores en cálculos estadísticos posteriores (como promedios), ya que distorsionarían los resultados.
*   **Imputación estadística (Media/Mediana):** Se reemplaza el valor faltante por el promedio del atributo. Es una técnica común, aunque puede crear picos artificiales en la distribución de los datos.
*   **Predicción basada en modelos (La más sofisticada):** Se considera el método más avanzado algorítmicamente. Consiste en utilizar otros atributos (como género, hábitos de fumar, etc.) para **predecir el valor faltante** mediante algoritmos de correlación multidimensional.

### 2. Manejo de Datos Atípicos (Outliers) y Ruidosos
Para suavizar los datos y reducir el impacto de valores extremos que puedan sesgar el modelo, se sugieren:

*   **Binning (Agrupación en contenedores):** Los datos se ordenan y se dividen en "bins" de igual ancho o profundidad. Para que sea efectivo contra los outliers, es preferible reemplazar los valores de cada bin por la **mediana** en lugar de la media, ya que la mediana es mucho menos sensible a valores extremos.
*   **Regresión:** Se ajusta una función (lineal o no lineal) a los datos para identificar la estructura subyacente y **suavizar el ruido**.
*   **Clustering (Agrupamiento):** Ayuda a identificar outliers de forma visual o algorítmica; los puntos que quedan fuera de los grupos densos se interpretan como ruido o errores de entrada.
*   **Normalización y Estandarización:** Técnicas como la **normalización Min-Max** pueden ayudar a comprimir el impacto de los outliers al mapear todos los valores a un rango fijo (como 0 a 1), asegurando que las características de gran escala no eclipsen a las pequeñas.

**Conclusión sobre la efectividad:**
La forma más efectiva suele ser el **enfoque predictivo** para datos faltantes, siempre que se valide que no se están reforzando correlaciones artificiales. Para los datos atípicos, el uso de la **mediana en técnicas de binning** o el uso de **clustering** para detectar y eliminar ruido son las estrategias más robustas mencionadas.

***

**Analogía:** Manejar datos faltantes o atípicos es como restaurar una pintura antigua: puedes dejar los huecos vacíos (ignorar), pintarlos de un solo color plano (usar constantes), o intentar deducir qué colores iban ahí observando el resto de la obra (predicción por modelos). La última opción es la más compleja, pero es la que mejor preserva la armonía de la imagen final.

---

> La decisión sobre cómo tratar datos faltantes y valores atípicos debe considerar siempre el impacto potencial sobre el sesgo y la representatividad del conjunto de datos.
