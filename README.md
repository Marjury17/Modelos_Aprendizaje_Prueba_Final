# Modelos_Aprendizaje_Prueba_Final
# 1) Introducción
Se tiene un dataset con muestras que provienen de mujeres con cáncer de mama. Se debe crear un modelo que sea capaz de identificar si un paciente tiene o no cáncer.

# 2) Preparación del dataset
## 2.1) Carga del dataset
El dataset consta de un total de 569 muestras. Hay un total de 32 características que caracterizan las muestras, la primera de las cuales es el ID de la muestra, la segunda es su diagnóstico y los 30 restantes son características que contienen diversa información sobre las muestras. La etiqueta de diagnóstico de las muestras puede ser maligna (M) o benigna (B).

## 2.2) Exploración inicial
El dataset consta de 569 filas y 32 columnas. Todos los atributos, excepto la columna de diagnóstico (Diagnosis), son de tipo numérico (int64), lo que sugiere que las características han sido preprocesadas para representar valores enteros. No se han detectado valores nulos en ninguna de las columnas.
Se tiene 357 muestras con diagnóstico Benigno y 212 Maligno.

## 2.3) Preprocesamiento
Se verifica que no se tiene valores nulos en el conjunto de datos.
Se elimina la columna 'ID', ya que no es una característica relevante para el análisis.
Se asigna valores binarios a la columna "Diagnosis" basados en el valor de la cadena en cada fila, el valor 1 si la fila contiene la letra 'M' y el valor 0 en caso contrario.
Se realiza un matriz de correlación para determinar la relación entre dos variables dadas en forma de matriz.
En el mapa de correlación, la forma en que se interpreta es cuanto mayor es el valor de correlación, más correlacionadas están las dos variables (características): El radio, el área y el perímetro están correlacionados (corr>0,9), esto es correcto porque el área y el perímetro se calculan utilizando los valores del radio.
Texture_1 y Texture_3 están altamente correlacionados con corr_value = 0,91 

Antes de aplicar los modelos de aprendizaje se divido el conjunto de datos para entrenamiento y test. Se tiene 398 muestras para train y 171 para test

# 3) Modelos de aprendizaje Seleccionados
## 3.1) Árbol de Decisión
•	Un árbol de decisión binario es un algoritmo de aprendizaje automático que organiza la información en una estructura jerárquica en forma de árbol. Cada nodo del árbol representa una decisión o una pregunta sobre los datos, y cada rama representa una posible respuesta a esa pregunta. A medida que se recorren las ramas, se toman decisiones sucesivas hasta llegar a una hoja del árbol, que representa una predicción o una clasificación.

## 3.2) Random Forest
•	Modelo de aprendizaje supervisado, utiliza datos etiquetados para "aprender" cómo clasificar datos no etiquetados. se utiliza para resolver problemas de regresión y clasificación, lo que lo convierte en un modelo diverso y ampliamente utilizado.

## 3.3) K-nearest Neighbors
•	El algoritmo de k-vecinos más cercanos (KNN) es un algoritmo de aprendizaje automático supervisado simple y fácil de implementar que se puede utilizar para resolver problemas de clasificación y regresión. 

# 4.) Análisis de Resultados
| Característica | Árbol de Decisión | Random Forest  | K-nearest Neighbors |
| -------------- | ----------------- | -------------- | ------------------- |
| Precisión | clase 0 (Benigno) es 0.97 - clase 1 (Maligno) es 0.90  | clase 0 (Benigno) es 0.96 - clase 1 (Maligno) es 0.98 | clase 0 (Benigno) es 0.94 - clase 1 (Maligno) es 0.98  |
| Recall  | clase 0 es 0.94 - clase 1 es 0.95 | clase 0 es 0.99 - clase 1 es 0.94  | clase 0 es 0.99 - clase 1 es 0.89 |
| F1-score | clase 0 es 0.95 - clase 1 es 0.92  | clase 0 es 0.98 - clase 1 es 0.96 | clase 0 es 0.96 - clase 1 es 0.93 |
| Support | 108 muestras de la clase 0 y 63 muestras de la clase 1 | 108 muestras de la clase 0 y 63 muestras de la clase 1 | 108 muestras de la clase 0 y 63 muestras de la clase 1  |
| Accuracy | 94% de las muestras en el conjunto de datos de prueba fueron predichas correctamente  | 97% de las muestras en el conjunto de datos de prueba fueron predichas correctamente | 95% de las muestras en el conjunto de datos de prueba fueron predichas correctamente |
| Matriz Confusión | 7 falsos positivos, lo que quiere decir que se detectó 7 personas con cáncer que en realidad no tenían. 3 falsos negativos, personas que si tienen cáncer y la predicción detectó que no tenían.  | 1 falso positivo, lo que quiere decir que se detectó una persona con cáncer que en realidad no tenía. 4 falsos negativos, personas que si tienen cáncer y la predicción detectó que no tenía. | 1 falso positivo, lo que quiere decir que se detectó una persona con cáncer que en realidad no tenía. 7 falsos negativos, personas que si tienen cáncer y la predicción detectó que no tenía. |

# 5.) Conclusión
Los 3 métodos de aprendizaje presentan una buena precisión y un buen accuracy, la selección del mejor modelo en este caso, depende del resultado de los falso positivos y falsos negativos.

Teniendo en cuenta que un falso positivo no es tan preocupante como un falso negativo, se concluye que para este caso el mejor modelo de aprendizaje es Random Forest, el cual tiene un accuracy general del 97%. Y detectó un 98% de las muestras benignas correctamente en cantidad son 4 personas que detectó que no tenian cáncer cuando si lo tienen.

En este caso Random Forest es una opción poderosa y versátil para problemas de clasificación y regresión que ofrece una mayor precisión, resistencia al sobreajuste y manejo automático de características en comparación con los otros 2 algoritmos de aprendizaje.

