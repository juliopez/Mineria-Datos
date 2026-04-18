# Data Dictionary – Dataset Deserción Estudiantil

## Descripción general

Este dataset contiene información académica y demográfica de estudiantes, con el objetivo de analizar factores asociados a la deserción durante el primer año en educación superior.

El dataset ha sido diseñado con fines educativos y puede contener inconsistencias intencionales para el desarrollo de habilidades de análisis de datos.

---

## Diccionario de variables

| Variable         | Tipo de dato | Nivel / subtipo | Descripción | Valores esperados / rango | Observaciones |
|------------------|--------------|-----------------|-------------|----------------------------|---------------|
| id_estudiante    | Numérico     | Entero / identificador | Identificador del estudiante | Valores enteros únicos | Puede presentar duplicados intencionales para fines pedagógicos |
| edad             | Numérico     | Entero          | Edad del estudiante | 17 a 30 años aprox. | Pueden existir valores atípicos o fuera de rango |
| asistencia       | Numérico     | Continuo        | Porcentaje de asistencia del estudiante | 0 a 100 | Puede contener valores nulos o fuera de rango |
| promedio_notas   | Numérico     | Continuo        | Promedio de notas del estudiante | Escala 1.0 a 7.0 | Puede incluir inconsistencias de escala (por ejemplo, valores en 0–100) |
| tipo_ingreso     | Categórico   | Nominal         | Vía de ingreso del estudiante | Regular, PACE, Traslado | Variable útil para segmentación |
| carrera          | Categórico   | Nominal         | Carrera o área de formación del estudiante | Ingeniería, Educación, Salud | Puede apoyar comparaciones entre grupos |
| estado_final     | Categórico   | Nominal         | Situación final del estudiante | Continúa, Desertó | Variable objetivo del análisis |


---

## Consideraciones de calidad de datos

El dataset puede presentar:

- Valores faltantes  
- Registros duplicados  
- Valores fuera de rango  
- Inconsistencias en variables categóricas  

Estas características son intencionales para fines pedagógicos.

---

## Uso en el curso

Este dataset se utiliza por primera vez en:

- Semana 2: Análisis exploratorio de datos (EDA)
- Identificación de variables
- Detección de problemas de calidad de datos
- Interpretación de resultados en contexto de deserción

---

## Enfoque analítico esperado

Se espera que el estudiante:

- Relacione variables con el problema de deserción  
- Identifique variables relevantes  
- Detecte problemas de calidad  
- Proponga interpretaciones basadas en evidencia  

---
