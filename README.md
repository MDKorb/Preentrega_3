# Recomendación de películas

En esta era de la conectividad constante, las plataformas ofrecen una amplia gama de programas, películas y documentales. El precio accesible, el amplio catálogo de contenidos, la flexibilidad de horarios, la ausencia de parones publicitarios y la comodidad de estar en tu propia casa son algunas de las ventajas del streaming respecto a la televisión. En ocasiones, el espectador encuentra dentro de la vorágine del día un espacio de desconexión y lo destina a ver una película, pero seleccionar que mirar puede representar gran parte del tiempo disponible. Por tal motivo, sería ventajoso contar con un análisis que permita al espectador guiarse en su elección de forma rápida según sus preferencias. También puede ser utilizado por las empresas cinematográficas.

## Objetivo

Por todo esto se planta como objetivo construir un modelo de aprendizaje supervisado para predecir la calificación promedio de una película, tomada como indicador de su aceptación por parte del público.

## Integrantes

Grupo 13

Natalia Machetti

Melisa Korb

## Selección de Dataset

El Dataset seleccionado fue extraído de https://www.kaggle.com/datasets/ky1338/10000-movies-letterboxd-data. Los datos se recopilaron en una lista de Letterboxd. Esta lista, diseñada como una ruleta de películas, cuenta con 10 002 entradas de diversos géneros y décadas. Los datos fueron tomados el 8/4/2025.

## Estructura del repositorio

Peliculas_3preentrega.ipynb: Notebook principal del proyecto, incluye limpieza, análisis exploratorio y modelado.

Movie_Data_File2.csv

README.md

## Metodología

Análisis exploratorio de datos

**Caracterización del DataFrame:** Se caracterizó el DataFrame según cantidad y tipo de variables.

**Análisis de variables categóricas:** en algunas columnas encontramos las variables categóricas como listas. Las separamos y conservamos el primer valor. Este procedimiento lo realizamos para las columnas Cast, Genres, Countries, Studios y Director. Cuando exploramos el resultado observamos valores repetidos, así que procedimos a unificarlos.

**Creación de una nueva variable:** creamos una nueva variable, Porcentaje_likes. Creemos que será de utilidad en el modelo predictivo.

**Eliminación y renombramiento de columnas:** eliminamos aquellas columnas que no serán de utilidad para la aplicación del modelo supervisado y renombramos en castellano las que conservamos.

**Datos faltantes:** realizamos el análisis de los datos faltantes numéricos y luego categóricos. En el primer caso aplicamos imputación simple. Respecto a los valores categóricos eran solo 2 por lo tanto procedimos a la eliminación de las filas que los contenían.

**Outliers:** primero identificamos aquellas columnas que tenían valores numéricos para luego proceder al análisis de cada una. De cada una visualizamos su distribución para luego definir el manejo. En caso de distribución normal utilizamos zscore para detectar outliers y en caso de distribución sesgada utilizamos rango intercuartílico. Se justificó en cada caso la no eliminación de los outliers. En el caso de la duración se detectó que había series en la lista por lo que en ese caso se procedió a identificarlas y eliminarlas.

### Escalado y transformación de datos

**Escalado de las variables:** las variables con distribución normal (Calificación_promedio y Duración) fueron Estandarizadas con z-score y las que presentaban sesgo (Vistas, Ratings, y Porcentaje_likes) Normalización con Min-MaxScaler.

**Exploración, eliminación y renombramiento luego de la Normalización y Estandarización:** se realizó una nueva exploración de las columnas y tipos de variables, se dejaron aquellas objeto de análisis ya estandarizadas o normalizadas. Se renombraron las columnas numéricas.

**Transformación con One Hot Encoding:** Debido a que las variables a transformar son categóricas y no tienen un orden predeterminado utilizamos OneHotEncoding. Las variables categóricas transformadas son 'Director', 'Genero', 'Pais', 'Lenguaje', 'Productora', 'Protagonista' y 'Coprotagonista'.

### Modelo de aprendizaje supervisado

Debido a que la variable a predecir ‘Calificación’ es numérica optamos por aplicar modelos de regresión.

#### Árbol de decisión

Aplicamos este modelo y obtuvimos como resultado un MSE de 0,31. Luego ajustamos algunos hiperparámetros y obtuvimos un mejor resultado (MSE=0,27).

#### Random Forest

El modelo Random Forest ajustó mejor que el árbol de decisión realizado anteriormente. El MSE disminuyó y el modelo explica el 78% de la varianza.

Luego realizamos el gráfico y visualizamos las 10 variables más importantes para la predicción del modelo.

#### Aplicación de GridSearchCV al Random Forest

A partir de este test optimizamos nuestro modelos y observamos que ……

#### Utilización de Cross_validation sobre el mejor modelo

## Herramientas utilizadas

Pandas

NumPy

Scikit-learn

Matplotlib

Seaborn

Entorno de trabajo: Colab / Jupyter 

