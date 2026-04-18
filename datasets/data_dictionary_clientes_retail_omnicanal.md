# Data Dictionary – Dataset Clientes Retail Omnicanal

## Descripción general

Este dataset simulado contiene información de clientes de una multitienda omnicanal, con compras en canales presenciales y online. Su propósito es apoyar actividades formativas de análisis exploratorio de datos (EDA), limpieza de datos y segmentación de clientes.

El conjunto de datos fue diseñado con fines educativos y contiene errores intencionales de calidad, tales como valores nulos, duplicados, inconsistencias categóricas y valores fuera de rango.

---

## Diccionario de variables

| Variable             | Tipo de dato | Subtipo / nivel | Descripción | Valores esperados / rango | Observaciones |
|---------------------|--------------|-----------------|-------------|----------------------------|---------------|
| id_cliente          | Numérico     | Entero / identificador | Identificador único del cliente | Valores enteros únicos | Puede presentar registros duplicados intencionales |
| edad                | Numérico     | Entero / razón | Edad del cliente | 18 a 75 aprox. | Puede contener valores nulos o fuera de rango |
| region              | Categórico   | Nominal | Región de residencia o referencia del cliente | Norte, Centro, Sur | Útil para segmentación geográfica |
| frecuencia_compra   | Numérico     | Entero / razón | Número de compras realizadas por el cliente en el período analizado | 0 o más | Puede contener valores fuera de rango o inconsistentes |
| monto_total         | Numérico     | Continuo / razón | Monto total gastado por el cliente en el período | Valores positivos | Puede incluir valores negativos intencionales para análisis de calidad |
| ticket_promedio     | Numérico     | Continuo / razón | Promedio de gasto por compra del cliente | Valores positivos | Puede contener nulos o inconsistencias con respecto a monto_total y frecuencia_compra |
| canal_preferido     | Categórico   | Nominal | Canal de compra preferido del cliente | Tienda, Online | Puede incluir inconsistencias de escritura (por ejemplo: online, OnLine, WEB, presencial) |
| categoria_frecuente | Categórico   | Nominal | Categoría de productos más comprada por el cliente | Tecnología, Vestuario, Hogar, Deportes | Variable útil para identificar patrones de consumo |
| uso_descuentos      | Categórico   | Ordinal | Nivel de uso de descuentos por parte del cliente | Alto, Medio, Bajo | Puede apoyar segmentación según sensibilidad al precio |
| devoluciones        | Numérico     | Entero / razón | Número de devoluciones realizadas por el cliente | 0 o más | Puede contener valores negativos intencionales para revisión de calidad |

---

## Consideraciones de calidad de datos

Este dataset puede presentar intencionalmente:

- valores faltantes
- registros duplicados
- inconsistencias en variables categóricas
- valores fuera de rango
- incoherencias entre variables numéricas

Estas situaciones forman parte del diseño pedagógico del recurso y permiten desarrollar habilidades de exploración, validación y limpieza de datos.

---

## Uso en el curso

Este dataset puede ser utilizado para:

- análisis exploratorio de datos (EDA)
- identificación de variables y tipos de datos
- detección de problemas de calidad de datos
- preparación y limpieza de datos
- segmentación de clientes
- interpretación de patrones de compra en contextos de gestión

---

## Propósito pedagógico

Se espera que el estudiante pueda:

- comprender el problema de negocio asociado al comportamiento de compra
- identificar variables relevantes para el análisis
- detectar errores y limitaciones en los datos
- explorar patrones de consumo
- proponer segmentaciones útiles para la toma de decisiones comerciales
