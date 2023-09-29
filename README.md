# Portfolio-datascience
Repositorio de proyectos
Aquí tienes el texto adaptado para tu archivo README:

```markdown
# Proyecto de Predicción de Malware de Microsoft

Este proyecto es una colaboración entre Kaggle y Microsoft, y su objetivo principal es abordar la predicción de malware desarrollado por Microsoft. Nuestra tarea central consiste en desarrollar modelos de aprendizaje automático capaces de identificar y clasificar eficazmente el malware en sistemas informáticos. Para ello, utilizamos datos proporcionados por Microsoft sobre la configuración de los equipos.

## Conjunto de Datos

El conjunto de datos consta de 500,000 observaciones y 83 variables, incluyendo nuestra variable objetivo, 'Has detection'. Notablemente, esta variable está perfectamente balanceada, con un 50% de observaciones en cada uno de sus valores posibles.

Sin embargo, se identificaron 8 variables con un alto porcentaje de valores faltantes (más del 30%). En consecuencia, decidimos eliminar estas variables del análisis. Luego, se realizó un análisis de la varianza de las variables restantes y se agruparon los valores poco frecuentes en variables categóricas bajo la categoría 'otros'. El mismo procedimiento se aplicó para abordar los valores faltantes en las variables categóricas.

## Análisis de Variables

Se llevó a cabo un estudio exhaustivo de la relación entre las variables seleccionadas y el objetivo ('Has detection'). Como resultado, se encontró que las relaciones más fuertes se observaron en las variables 'AVProductsInstalled', 'AVProductStatesIdentifier' y 'EngineVersion'.

## Preprocesamiento de Datos

Para abordar las variables categóricas, se aplicó la codificación 'One-Hot Encoding' (OHE). Además, se implementaron estrategias de preprocesamiento para manejar los valores faltantes y las variables con baja varianza.

## Evaluación y Selección de Modelo

En cuanto a la estrategia de evaluación, se utilizó la división de datos en entrenamiento y prueba (Hold Out) con un 20% de los datos reservados para prueba. Además, se aplicó la validación cruzada K-fold y se utilizó el área bajo la curva (AUC) como métrica principal para seleccionar el mejor modelo.

Luego de evaluar tres modelos (Árbol de decisión, Random Forest y Gradient Boosting) optimizándolos mediante la técnica de búsqueda aleatoria (Randomized Search), se seleccionó el modelo Gradient Boosting como el que arrojó los mejores resultados. Este modelo logró un AUC de 0.67, lo que indica un rendimiento cercano al de una selección aleatoria de categorías.

## Umbral de Clasificación

La elección del umbral óptimo para poner en producción el modelo dependerá del análisis de costos asociados a los errores de clasificación. Por ejemplo, si el costo de permitir que un ordenador se infecte es alto, se podría preferir un umbral más bajo para maximizar el recall, incluso a expensas de la precisión.

Con un umbral de 0.1, el modelo captura el 100% de los ordenadores infectados (recall 1), pero su precisión es del 0.5, lo que significa que solo el 50% de las predicciones positivas son correctas. El problema es que clasifica el 100% de los ordenadores como infectados.

Aumentar el umbral a 0.35 capturaría el 91% de los ordenadores infectados, con una precisión del 54%, lo que indicaría que el 84% de los ordenadores se considerarían infectados.

Este análisis sugiere que la elección del umbral debe basarse en los objetivos específicos y los costos asociados con los errores de clasificación.
```

Por favor, si necesitas alguna modificación adicional o más ayuda, házmelo saber.
