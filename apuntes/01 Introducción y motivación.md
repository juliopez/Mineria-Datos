---
titulo: Minería de Datos – 01. Introducción y motivación
serie: Minería de Datos – Introducción
playlist: https://www.youtube.com/playlist?list=PLrc3rKEj3Qc9DCowe-5CIWmYlngJLLOw8
tipo: Apuntes introductorios
nivel: Introductorio
---
### I. Introducción a la Minería de Datos

**Motivación (El Problema del Dato):**
*   La principal motivación para la minería de datos es la **abundancia masiva de datos** generados continuamente (por ejemplo, millones de correos electrónicos y búsquedas de Google por minuto).
*   Esta cantidad masiva de datos brutos hace que el análisis manual sea imposible.
*   El objetivo es **dar sentido a los datos** y extraer conocimiento útil.

**Definiciones y Conceptos Relacionados:**
*   **Minería de Datos (Data Mining):** Es el proceso de descubrir patrones, tendencias y relaciones en grandes conjuntos de datos utilizando técnicas estadísticas y computacionales, con el fin de extraer conocimiento útil, a menudo para la toma de decisiones.
*   La minería de datos se relaciona con la analogía de la minería de carbón: encontrar "pepitas ocultas" (insights informativos) en toneladas de roca (datos).
*   **Objetivo:** Descubrir patrones, tendencias y anomalías **útiles y sorprendentes**. Se busca obtener **conocimiento accionable** (actionable knowledge).
*   Conceptos relacionados: **Big Data** (datos demasiado grandes para herramientas tradicionales), **Business Intelligence** (centrado en informes y KPIs), y **Aprendizaje Automático (Machine Learning)** (una rama exitosa de la IA que utiliza Big Data como entrada).
*   El curso se centra más en la **práctica** que en las demostraciones matemáticas.

### II. Tareas Principales de la Minería de Datos

Existen tres tareas principales de minería de datos:

1.  **Tareas Descriptivas (Aprendizaje No Supervisado):**
    *   Implican la exploración de datos para comprenderlos y encontrar patrones o tendencias.
    *   Ejemplos de métodos: Clustering (agrupación), Association Mining (minería de asociaciones), y estadística descriptiva.
    *   *Ejemplo:* Encontrar qué productos se compran juntos en un supermercado (Association Mining).

2.  **Tareas Predictivas (Aprendizaje Supervisado):**
    *   Implican una tarea clara: predecir valores desconocidos basándose en datos etiquetados del pasado.
    *   Ejemplos de métodos: Classification (Clasificación), Regression (Regresión), y modelos generativos.
    *   *Ejemplo:* Predecir si un nuevo cliente obtendrá un crédito (Clasificación, si la salida es Sí/No).

**Ejemplos de Aplicación y Tareas Específicas:**
*   **Supermercados:** Se utiliza Association Mining (qué artículos se asocian) para organizar la tienda, a menudo separando artículos relacionados para fomentar la venta cruzada. También se usa Clasificación (categorizar nuevos productos o clientes) y Detección de Valores Atípicos (identificar comportamientos inusuales).
*   **Tráfico de Redes:** Un ejemplo de Big Data; se utiliza Clasificación (identificar el tipo de paquete o actividad) y Detección de Anomalías (detectar picos o flujos inesperados, como intentos de hackeo).
*   **Precios Inmobiliarios:** Predecir un valor continuo (el precio) es un problema de **Regresión**.
*   **Clasificación de Enfermedades:** Distinguir pacientes con clases conocidas (p. ej., AML vs. ALL) es una tarea de **Clasificación**.
*   **Identificación de Usuarios Maliciosos:** Si no se conocen las clases de usuarios, encontrar grupos sospechosos es **Clustering**.

### III. Proceso de Descubrimiento de Conocimiento (KDD)

El proceso KDD (Knowledge Discovery in Databases) es el flujo completo desde los datos brutos hasta el conocimiento.
1.  **Datos Brutos (Raw Data):** Lo que se recolecta.
2.  **Datos Dirigidos (Targeted Data):** Selección de un subconjunto enfocado de los datos.
3.  **Pre-procesamiento (Pre-processing):** Limpieza de datos (eliminar ruido) y agregación de datos.
4.  **Datos Transformados (Transformed Data):** Organización de los datos en un formato regular.
5.  **Minería de Datos (Data Mining):** Extracción de patrones.
6.  **Interpretación/Evaluación:** La interpretación humana y la visualización de los resultados.

**Un punto crucial es que el pre-procesamiento y la transformación de datos consumen aproximadamente el 80% del tiempo** en entornos reales de minería de datos.
