Este proyecto en colaboración entre Kaggle y Microsoft se enfoca en la predicción de malware desarrollado por Microsoft. La tarea principal consiste en desarrollar modelos de aprendizaje automático capaces de identificar y clasificar eficazmente el malware en sistemas informáticos, utilizando datos proporcionados por Microsoft sobre la configuración de los equipos.

El conjunto de datos consta de 500,000 observaciones y 83 variables, incluyendo nuestra variable objetivo, 'Has detection'. Esta variable está perfectamente balanceada, con un 50% de observaciones en cada uno de sus valores posibles.

Sin embargo, se identificaron 8 variables con un alto porcentaje de valores faltantes (más del 30%), por lo que decidimos eliminarlas del análisis. Luego, se realizó un análisis de la varianza de las variables restantes y se agruparon los valores poco frecuentes en variables categóricas bajo la categoría 'otros'. Lo mismo se hizo para los valores faltantes en las variables categóricas.

Se llevó a cabo un estudio de la relación entre las variables seleccionadas y el objetivo ('Has detection'). Se encontró que las relaciones más fuertes se observaron en las variables 'AVProductsInstalled', 'AVProductStatesIdentifier' y 'EngineVersion'.




Para abordar las variables categóricas, se aplicó la codificación 'One-Hot Encoding' (OHE).

En cuanto a la estrategia de evaluación, se utilizó la división de datos en entrenamiento y prueba (Hold Out) con un 20% de los datos reservados para prueba. Además, se aplicó la validación cruzada K-fold y se utilizó el área bajo la curva (AUC) como métrica principal para seleccionar el mejor modelo.

Luego de evaluar tres modelos (Árbol de decisión, Random Forest y Gradient Boosting) optimizándolos mediante la técnica de búsqueda aleatoria (Randomized Search), se seleccionó el modelo Gradient Boosting como el que arrojó los mejores resultados. Este modelo logró un AUC de 0.67, lo que indica un rendimiento cercano al de una selección aleatoria de categorías. Con un umbral de 0.5, se obtuvieron los siguientes resultados:
- Exactitud (Accuracy): 0.62
- Recall: 0.65
- Precisión: 0.61

La elección del umbral óptimo para poner en producción el modelo dependerá del análisis de costos asociados a los errores de clasificación. Por ejemplo, si el costo de permitir que un ordenador se infecte es alto, se podría preferir un umbral más bajo para maximizar el recall, incluso a expensas de la precisión.

Con un umbral de 0.1, el modelo captura el 100% de los ordenadores infectados (recall 1), pero su precisión es del 0.5, lo que significa que solo el 50% de las predicciones positivas son correctas. El problema es que clasifica el 100% de los ordenadores como infectados.


Aumentar el umbral a 0.35 capturaría el 91% de los ordenadores infectados, con una precisión del 54%, lo que indicaría que el 84% de los ordenadores se considerarían infectados.


Este análisis sugiere que la elección del umbral debe basarse en los objetivos específicos y los costos asociados con los errores de clasificación.
