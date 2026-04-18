# Data Dictionary – Dataset Deserción Estudiantil

## Descripción general

Este dataset contiene información académica y demográfica de estudiantes, con el objetivo de analizar factores asociados a la deserción durante el primer año en educación superior.

El dataset ha sido diseñado con fines educativos y puede contener inconsistencias intencionales para el desarrollo de habilidades de análisis de datos.

---

## Diccionario de variables

| Variable                    | Tipo        | Subtipo        | Descripción                                                                 | Valores posibles / Rango                 | Observaciones |
|----------------------------|------------|---------------|-----------------------------------------------------------------------------|------------------------------------------|--------------|
| id_estudiante              | Identificador | Entero        | Identificador único del estudiante                                          | Valores únicos                           | Puede utilizarse como clave primaria |
| edad                       | Numérico    | Entero        | Edad del estudiante al momento de ingreso                                   | 17 – 40                                  | Revisar valores atípicos |
| genero                     | Categórico  | Nominal       | Género del estudiante                                                       | Masculino, Femenino                      | Posibles valores inconsistentes |
| tipo_colegio               | Categórico  | Nominal       | Tipo de establecimiento de egreso                                           | Municipal, Subvencionado, Particular     | Puede influir en desempeño |
| promedio_notas             | Numérico    | Continuo      | Promedio de notas en enseñanza media                                        | 4.0 – 7.0                                | Escala chilena |
| puntaje_ingreso            | Numérico    | Entero        | Puntaje de ingreso a la universidad                                         | 400 – 850                                | Similar a pruebas estandarizadas |
| asistencia                 | Numérico    | Continuo      | Porcentaje de asistencia durante el primer año                              | 0 – 100                                  | Valores fuera de rango indican error |
| creditos_aprobados         | Numérico    | Entero        | Número de créditos aprobados en el periodo                                  | 0 – 60                                   | Variable clave de rendimiento |
| nivel_socioeconomico       | Categórico  | Ordinal       | Nivel socioeconómico del estudiante                                         | Bajo, Medio, Alto                        | Orden implícito |
| trabaja                    | Categórico  | Binario       | Indica si el estudiante trabaja mientras estudia                            | Sí, No                                   | Puede afectar desempeño |
| distancia_universidad      | Numérico    | Continuo      | Distancia desde el hogar a la universidad (km)                              | 0 – 50                                   | Aproximado |
| estado_final               | Categórico  | Nominal       | Estado académico del estudiante                                             | Activo, Desertor, Titulado               | Variable objetivo en análisis |

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
