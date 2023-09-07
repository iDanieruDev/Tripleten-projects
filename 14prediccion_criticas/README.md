# Descripción del proyecto
Film Junky Union, una nueva comunidad vanguardista para los aficionados de las películas clásicas, está desarrollando un sistema para filtrar y categorizar reseñas de películas. Tu objetivo es entrenar un modelo para detectar las críticas negativas de forma automática. Para lograrlo, utilizarás un conjunto de datos de reseñas de películas de IMDB con leyendas de polaridad para construir un modelo para clasificar las reseñas positivas y negativas. Este deberá alcanzar un valor F1 de al menos 0.85.

<h1>Tabla de contenidos<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><span><a href="#Inicialización" data-toc-modified-id="Inicialización-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>Inicialización</a></span></li><li><span><a href="#Cargar-datos" data-toc-modified-id="Cargar-datos-2"><span class="toc-item-num">2&nbsp;&nbsp;</span>Cargar datos</a></span></li><li><span><a href="#EDA-(Exploratory-Data-Analysis)" data-toc-modified-id="EDA-(Exploratory-Data-Analysis)-3"><span class="toc-item-num">3&nbsp;&nbsp;</span>EDA (Exploratory Data Analysis)</a></span><ul class="toc-item"><li><span><a href="#Analisis-del-dataset-en-general" data-toc-modified-id="Analisis-del-dataset-en-general-3.1"><span class="toc-item-num">3.1&nbsp;&nbsp;</span>Analisis del dataset en general</a></span></li><li><span><a href="#Analisis-de-las-variables-de-interes" data-toc-modified-id="Analisis-de-las-variables-de-interes-3.2"><span class="toc-item-num">3.2&nbsp;&nbsp;</span>Analisis de las variables de interes</a></span></li></ul></li><li><span><a href="#Procedimiento-de-evaluación" data-toc-modified-id="Procedimiento-de-evaluación-4"><span class="toc-item-num">4&nbsp;&nbsp;</span>Procedimiento de evaluación</a></span></li><li><span><a href="#Normalización" data-toc-modified-id="Normalización-5"><span class="toc-item-num">5&nbsp;&nbsp;</span>Normalización</a></span></li><li><span><a href="#División-entrenamiento-/-prueba" data-toc-modified-id="División-entrenamiento-/-prueba-6"><span class="toc-item-num">6&nbsp;&nbsp;</span>División entrenamiento / prueba</a></span></li><li><span><a href="#Trabajar-con-modelos" data-toc-modified-id="Trabajar-con-modelos-7"><span class="toc-item-num">7&nbsp;&nbsp;</span>Trabajar con modelos</a></span><ul class="toc-item"><li><span><a href="#Modelo-1---Constante" data-toc-modified-id="Modelo-1---Constante-7.1"><span class="toc-item-num">7.1&nbsp;&nbsp;</span>Modelo 1 - Constante</a></span></li><li><span><a href="#Modelo-2---NLTK,-TF-IDF-y-Regresión-Logistica" data-toc-modified-id="Modelo-2---NLTK,-TF-IDF-y-Regresión-Logistica-7.2"><span class="toc-item-num">7.2&nbsp;&nbsp;</span>Modelo 2 - NLTK, TF-IDF y Regresión Logistica</a></span><ul class="toc-item"><li><span><a href="#Construcción-y-entrenamiento-del-modelo" data-toc-modified-id="Construcción-y-entrenamiento-del-modelo-7.2.1"><span class="toc-item-num">7.2.1&nbsp;&nbsp;</span>Construcción y entrenamiento del modelo</a></span></li><li><span><a href="#Evaluación-del-modelo-y-conclusiones" data-toc-modified-id="Evaluación-del-modelo-y-conclusiones-7.2.2"><span class="toc-item-num">7.2.2&nbsp;&nbsp;</span>Evaluación del modelo y conclusiones</a></span></li></ul></li><li><span><a href="#Modelo-3---spaCy,-TF-IDF-y-Regresión-Logistica" data-toc-modified-id="Modelo-3---spaCy,-TF-IDF-y-Regresión-Logistica-7.3"><span class="toc-item-num">7.3&nbsp;&nbsp;</span>Modelo 3 - spaCy, TF-IDF y Regresión Logistica</a></span><ul class="toc-item"><li><span><a href="#Construcción-y-entrenamiento-del-modelo" data-toc-modified-id="Construcción-y-entrenamiento-del-modelo-7.3.1"><span class="toc-item-num">7.3.1&nbsp;&nbsp;</span>Construcción y entrenamiento del modelo</a></span></li><li><span><a href="#Evaluación-del-modelo-y-conclusiones" data-toc-modified-id="Evaluación-del-modelo-y-conclusiones-7.3.2"><span class="toc-item-num">7.3.2&nbsp;&nbsp;</span>Evaluación del modelo y conclusiones</a></span></li></ul></li><li><span><a href="#Modelo-4---spaCy,-TF-IDF-y-LGBMClassifier" data-toc-modified-id="Modelo-4---spaCy,-TF-IDF-y-LGBMClassifier-7.4"><span class="toc-item-num">7.4&nbsp;&nbsp;</span>Modelo 4 - spaCy, TF-IDF y LGBMClassifier</a></span><ul class="toc-item"><li><span><a href="#Construcción-y-entrenamiento-del-modelo" data-toc-modified-id="Construcción-y-entrenamiento-del-modelo-7.4.1"><span class="toc-item-num">7.4.1&nbsp;&nbsp;</span>Construcción y entrenamiento del modelo</a></span></li><li><span><a href="#Evaluación-del-modelo-y-conclusiones" data-toc-modified-id="Evaluación-del-modelo-y-conclusiones-7.4.2"><span class="toc-item-num">7.4.2&nbsp;&nbsp;</span>Evaluación del modelo y conclusiones</a></span></li></ul></li><li><span><a href="#Modelo-9---BERT-+-Regresión-Logistica" data-toc-modified-id="Modelo-9---BERT-+-Regresión-Logistica-7.5"><span class="toc-item-num">7.5&nbsp;&nbsp;</span>Modelo 9 - BERT + Regresión Logistica</a></span><ul class="toc-item"><li><span><a href="#Vectorización-de-las-reviews-de-entrenamiento" data-toc-modified-id="Vectorización-de-las-reviews-de-entrenamiento-7.5.1"><span class="toc-item-num">7.5.1&nbsp;&nbsp;</span>Vectorización de las reviews de entrenamiento</a></span></li><li><span><a href="#Construcción-y-entrenamiento-del-modelo" data-toc-modified-id="Construcción-y-entrenamiento-del-modelo-7.5.2"><span class="toc-item-num">7.5.2&nbsp;&nbsp;</span>Construcción y entrenamiento del modelo</a></span></li><li><span><a href="#Evaluación-del-modelo-y-conclusiones" data-toc-modified-id="Evaluación-del-modelo-y-conclusiones-7.5.3"><span class="toc-item-num">7.5.3&nbsp;&nbsp;</span>Evaluación del modelo y conclusiones</a></span></li></ul></li></ul></li><li><span><a href="#Mis-reseñas" data-toc-modified-id="Mis-reseñas-8"><span class="toc-item-num">8&nbsp;&nbsp;</span>Mis reseñas</a></span><ul class="toc-item"><li><span><a href="#Modelo-2" data-toc-modified-id="Modelo-2-8.1"><span class="toc-item-num">8.1&nbsp;&nbsp;</span>Modelo 2</a></span></li><li><span><a href="#Modelo-3" data-toc-modified-id="Modelo-3-8.2"><span class="toc-item-num">8.2&nbsp;&nbsp;</span>Modelo 3</a></span></li><li><span><a href="#Modelo-4" data-toc-modified-id="Modelo-4-8.3"><span class="toc-item-num">8.3&nbsp;&nbsp;</span>Modelo 4</a></span></li><li><span><a href="#Modelo-9" data-toc-modified-id="Modelo-9-8.4"><span class="toc-item-num">8.4&nbsp;&nbsp;</span>Modelo 9</a></span></li></ul></li><li><span><a href="#Conclusiones" data-toc-modified-id="Conclusiones-9"><span class="toc-item-num">9&nbsp;&nbsp;</span>Conclusiones</a></span></li></ul></div>

## Descripción de los datos

Los datos se almacenan en el archivo `imdb_reviews.tsv`.

El DataFrame dispone de 17 campos, sin embargo, utilizaremos solo 3, estos son:  
- `review`: el texto de la reseña  
- `pos`: el objetivo, '0' para negativo y '1' para positivo  
- `ds_part`: 'entrenamiento'/'prueba' para la parte de entrenamiento/prueba del conjunto de datos, respectivamente  

## Librerias usadas

- pandas
- matplotlib.pyplot
- numpy
- math
- seaborn
- tqdm
- re
- sklearn
- nltk
- spaCy
- lightgbm
- torch
- transformers

# Conclusiones

Los modelos 2 y 3 (utilizando NLTK o spaCy junto con TF-IDF y Regresión Lineal) parecen ser los más consistentes y efectivos. El modelo con LGBMClassifier también están haciendo un buen trabajo, pero están un poco por debajo de los otros. Por último, el modelo basado en BERT también tiene un rendimiento decente, pero ligeramente inferior en este conjunto de datos.

Teniendo en cuenta que los modelos 2 y 3 son los que mejores métricas presentan, son los ideales para esta tarea de clasificación, tanto por sus metricas como por su simplicidad en comparación con el resto de modelos.

Por último, a pesar de que el desempeño del modelo usando BERT teoricamente es inferior, en las pruebas con reseñas personalizadas, me pareció que este modelo generaliza mejor. Pareciera que este modelo "duda" menos al momento de determinar la probabilidad de una review, asignando probabilidades con mayor "seguridad" al momento de determinar el sentimiento de una reseña. En particular llamó mi atención la reseña 5.  

*Reseña 5: 'Estaba realmente fascinada con la película'*  

Reseña que los otros modelos no evaluaron del todo bien, este le da un probabilidad de casi un 100% (de que sea positiva).
