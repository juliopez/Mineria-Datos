---
titulo: Minería de Datos – 04. Métodos de clasificación
serie: Minería de Datos – Introducción
playlist: https://www.youtube.com/playlist?list=PLrc3rKEj3Qc9DCowe-5CIWmYlngJLLOw8
tipo: Apuntes introductorios
nivel: Introductorio
---
### Árboles de Decisión (Decision Trees)

Los árboles de decisión son uno de los métodos de clasificación que utilizan reglas de decisión simples basadas en atributos de entrada para predecir un atributo de clase.

**Construcción del Árbol y Ganancia de Información (Information Gain):**

Para construir un árbol de decisión, se busca un atributo que proporcione la **mayor cantidad de información** sobre el atributo de clase.

1.  **Manejo de Variables Numéricas:** Las variables numéricas (como la edad) no deben dividirse en demasiados valores, por lo que se utiliza la categorización o *binning* (por ejemplo, "joven" o "senior"). El algoritmo debe decidir los puntos de corte, lo que puede implicar una búsqueda exhaustiva de todos los posibles puntos de división para calcular la ganancia y elegir el mejor.
2.  **Entropía:** Para medir qué tan informativo es un atributo, se utiliza la entropía. La entropía es una medida de la **incertidumbre** o aleatoriedad de un valor.
    *   Si un valor es muy uniforme (distribución igualitaria, por ejemplo, mitad "sí", mitad "no"), tiene una entropía **alta** (máxima).
    *   Si solo hay un valor (por ejemplo, todos son "sí"), la entropía es **baja** (cero).
    *   Shannon introdujo este concepto, donde una alta entropía indica que se necesitan muchos bits para codificar la información.
3.  **Cálculo de la Ganancia:** La **ganancia de información** se calcula restando la entropía después de la división (según un atributo) de la entropía que se tenía antes. El objetivo es elegir el atributo que maximice esta ganancia. La entropía después de la división se calcula tomando la entropía de cada partición (subconjunto) y ponderándola por la proporción de datos que van a esa partición.
4.  **Criterio de Parada:** La construcción del árbol continúa de forma recursiva hasta que un nodo se vuelve "puro" (solo contiene una clase, por ejemplo, solo "sí" o solo "no"), momento en el que la entropía es cero y no hay nada más que ganar.

**Sobreajuste (Overfitting) y Poda (Pruning):**

*   **Sobreajuste:** A medida que la profundidad del árbol aumenta, la precisión en los datos de entrenamiento (*training data*) mejora, pero la precisión en los datos de prueba (*test data*) a menudo disminuye o se estabiliza. Esto se conoce como **sobreajuste**, donde el árbol se ajusta tan perfectamente a los datos de entrenamiento que no generaliza bien a los datos no vistos.
*   **Poda (Pruning):** Para evitar el sobreajuste, se eliminan las ramas menos confiables.
    *   **Poda anticipada (Pre-pruning):** Se detiene la construcción antes de tiempo modificando los criterios de parada, por ejemplo, exigiendo un **soporte mínimo** (tamaño mínimo de la muestra en un nodo hoja) o una **confianza mínima** (porcentaje de pureza).
    *   **Poda posterior (Post-pruning):** Se construye el árbol completo y luego se cortan las ramas. Esto se decide minimizando la **complejidad de costos** (*cost complexity*), una fórmula que equilibra el error introducido por la poda con la ganancia en el tamaño (número de hojas) del árbol.

**Ventajas y Desventajas de los Árboles:**

*   **Ventajas:** Son relativamente fáciles de entender (son una "caja blanca" o *white box*) y proporcionan **explicabilidad**. Esta explicabilidad es crucial en aplicaciones donde se debe justificar una decisión (como en la ley europea), a diferencia de las redes neuronales. Son robustos ante ligeros cambios en los datos y su construcción es relativamente económica.
*   **Desventajas:** Existe el riesgo de sobreajuste. Los árboles grandes son difíciles de analizar. Pueden ser inestables (un pequeño cambio en los datos puede hacer que todo el árbol cambie si afecta el nodo raíz). También puede haber repetición de criterios de división en diferentes subárboles.

**Ensembles (Conjuntos de Modelos):**

En muchas aplicaciones del mundo real, se utilizan conjuntos (*ensembles*) de árboles de decisión para mejorar significativamente la precisión y la robustez.

*   **Agregación (Bagging / Random Forests):** Implica entrenar múltiples clasificadores (árboles) utilizando diferentes **subconjuntos muestreados aleatoriamente** de los datos de entrenamiento. La predicción final es la clase de mayoría (votación) entre todos los modelos.
*   **Boosting:** Es una técnica de entrenamiento secuencial. Los aprendices posteriores (árboles) se enfocan específicamente en clasificar correctamente las muestras que fueron clasificadas **incorrectamente** por los árboles anteriores.

---

### Introducción a la Clasificación Bayesiana

El objetivo de la clasificación es encontrar el valor de clase $Y$ (por ejemplo, rating de crédito) dado un vector de valores de entrada $X$ (edad, estudiante, etc.).

**Teorema de Bayes:**

El Teorema de Bayes permite calcular la **probabilidad posterior** $P(H|X)$ (la probabilidad de que la hipótesis $H$ sea verdadera dadas las observaciones $X$).

$$P(H|X) = \frac{P(X|H) \cdot P(H)}{P(X)}$$

*   $P(X|H)$: Es la **verosimilitud** (*likelihood*).
*   $P(H)$: Es la **probabilidad previa** (*prior*), la probabilidad de la hipótesis antes de ver los datos.
*   $P(X)$: Es la probabilidad marginal de observar los datos.

En clasificación, se quiere asignar una muestra $X$ a la clase $C_j$ con la **mayor probabilidad posterior**. Dado que $P(X)$ es constante para todas las clases, se puede ignorar en el proceso de maximización, haciendo que la clasificación sea proporcional a $P(X|C_j) \cdot P(C_j)$.

**El Problema de la Combinación Completa:**

Para una clasificación óptima, se requeriría calcular la probabilidad condicional de la combinación exacta de todos los atributos de entrada, $P(X_1, X_2, ..., X_n | C_j)$. El problema es que en la práctica, especialmente con un gran número de atributos, la mayoría de las combinaciones posibles **no existen** en el conjunto de datos de entrenamiento (resultando en probabilidades de cero). Almacenar todas estas probabilidades condicionales requeriría un espacio exponencial en el número de atributos, lo cual es inviable.

**Clasificación Naive Bayes:**

Para solucionar esto, se introduce la **Suposición Naive Bayes**. Esta suposición sostiene que los atributos son **condicionalmente independientes** entre sí.

Aunque esta suposición a menudo no se cumple en la realidad (por ejemplo, la edad y los ingresos suelen estar correlacionados), permite simplificar el cálculo: en lugar de calcular la probabilidad de la combinación completa, simplemente se **multiplican** las probabilidades condicionales de los atributos individuales.

$$P(X|C_j) \approx \prod_{i=1}^{n} P(X_i|C_j)$$

De esta manera, las probabilidades de cada atributo dado cada clase se pueden precalcular fácilmente en el tiempo de entrenamiento y utilizarse para predecir nuevos puntos de datos de manera eficiente.
