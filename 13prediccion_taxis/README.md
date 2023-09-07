# Descripción del proyecto

La compañía Sweet Lift Taxi ha recopilado datos históricos sobre pedidos de taxis en los aeropuertos. Para atraer a más conductores durante las horas pico, necesitamos predecir la cantidad de pedidos de taxis para la próxima hora. Construiré un modelo para dicha predicción.

La métrica RECM en el conjunto de prueba no debe ser superior a 48.

<h1>Tabla de contenidos<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><span><a href="#Inicialización" data-toc-modified-id="Inicialización-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>Inicialización</a></span></li><li><span><a href="#Preparación" data-toc-modified-id="Preparación-2"><span class="toc-item-num">2&nbsp;&nbsp;</span>Preparación</a></span><ul class="toc-item"><li><span><a href="#Carga-de-datos" data-toc-modified-id="Carga-de-datos-2.1"><span class="toc-item-num">2.1&nbsp;&nbsp;</span>Carga de datos</a></span></li><li><span><a href="#Estandarizamos-fechas-y-definimos-indices" data-toc-modified-id="Estandarizamos-fechas-y-definimos-indices-2.2"><span class="toc-item-num">2.2&nbsp;&nbsp;</span>Estandarizamos fechas y definimos indices</a></span></li><li><span><a href="#Remuestro-por-horas" data-toc-modified-id="Remuestro-por-horas-2.3"><span class="toc-item-num">2.3&nbsp;&nbsp;</span>Remuestro por horas</a></span></li></ul></li><li><span><a href="#Análisis" data-toc-modified-id="Análisis-3"><span class="toc-item-num">3&nbsp;&nbsp;</span>Análisis</a></span><ul class="toc-item"><li><span><a href="#Media-Movil" data-toc-modified-id="Media-Movil-3.1"><span class="toc-item-num">3.1&nbsp;&nbsp;</span>Media Movil</a></span></li><li><span><a href="#Tendencias-y-estacionalidad" data-toc-modified-id="Tendencias-y-estacionalidad-3.2"><span class="toc-item-num">3.2&nbsp;&nbsp;</span>Tendencias y estacionalidad</a></span></li></ul></li><li><span><a href="#Formación" data-toc-modified-id="Formación-4"><span class="toc-item-num">4&nbsp;&nbsp;</span>Formación</a></span></li><li><span><a href="#Entrenamiento-y-pruebas" data-toc-modified-id="Entrenamiento-y-pruebas-5"><span class="toc-item-num">5&nbsp;&nbsp;</span>Entrenamiento y pruebas</a></span><ul class="toc-item"><li><span><a href="#Definimos-nuestro-set-de-entrenamiento-y-validación" data-toc-modified-id="Definimos-nuestro-set-de-entrenamiento-y-validación-5.1"><span class="toc-item-num">5.1&nbsp;&nbsp;</span>Definimos nuestro set de entrenamiento y validación</a></span></li><li><span><a href="#Entrenamientos-preliminares" data-toc-modified-id="Entrenamientos-preliminares-5.2"><span class="toc-item-num">5.2&nbsp;&nbsp;</span>Entrenamientos preliminares</a></span><ul class="toc-item"><li><span><a href="#Modelo-Arbol-de-decisión" data-toc-modified-id="Modelo-Arbol-de-decisión-5.2.1"><span class="toc-item-num">5.2.1&nbsp;&nbsp;</span>Modelo Arbol de decisión</a></span></li><li><span><a href="#Modelo-Bosques-Aleatorios" data-toc-modified-id="Modelo-Bosques-Aleatorios-5.2.2"><span class="toc-item-num">5.2.2&nbsp;&nbsp;</span>Modelo Bosques Aleatorios</a></span></li><li><span><a href="#Modelo-de-Regresión-Lineal" data-toc-modified-id="Modelo-de-Regresión-Lineal-5.2.3"><span class="toc-item-num">5.2.3&nbsp;&nbsp;</span>Modelo de Regresión Lineal</a></span></li><li><span><a href="#Modelo-de-potenciación-del-grandiente-(LightGBM)" data-toc-modified-id="Modelo-de-potenciación-del-grandiente-(LightGBM)-5.2.4"><span class="toc-item-num">5.2.4&nbsp;&nbsp;</span>Modelo de potenciación del grandiente (LightGBM)</a></span></li></ul></li><li><span><a href="#Busqueda-de-hiperparametros-idoneos-para-cada-modelo-con-GridSearchCV" data-toc-modified-id="Busqueda-de-hiperparametros-idoneos-para-cada-modelo-con-GridSearchCV-5.3"><span class="toc-item-num">5.3&nbsp;&nbsp;</span>Busqueda de hiperparametros idoneos para cada modelo con GridSearchCV</a></span><ul class="toc-item"><li><span><a href="#Definimos-el-score-RMSE-a-optimizar-con-GridSeach" data-toc-modified-id="Definimos-el-score-RMSE-a-optimizar-con-GridSeach-5.3.1"><span class="toc-item-num">5.3.1&nbsp;&nbsp;</span>Definimos el score RMSE a optimizar con GridSeach</a></span></li><li><span><a href="#Modelo-Arbol-de-decisión-(GridSearchCV)" data-toc-modified-id="Modelo-Arbol-de-decisión-(GridSearchCV)-5.3.2"><span class="toc-item-num">5.3.2&nbsp;&nbsp;</span>Modelo Arbol de decisión (GridSearchCV)</a></span></li><li><span><a href="#Modelo-Bosques-Aleatorios-(GridSearchCV)" data-toc-modified-id="Modelo-Bosques-Aleatorios-(GridSearchCV)-5.3.3"><span class="toc-item-num">5.3.3&nbsp;&nbsp;</span>Modelo Bosques Aleatorios (GridSearchCV)</a></span></li><li><span><a href="#Modelo-de-Regresion-Lineal-(GridSearchCV)" data-toc-modified-id="Modelo-de-Regresion-Lineal-(GridSearchCV)-5.3.4"><span class="toc-item-num">5.3.4&nbsp;&nbsp;</span>Modelo de Regresion Lineal (GridSearchCV)</a></span></li><li><span><a href="#Modelo-LightGBM-(GridSearchCV)" data-toc-modified-id="Modelo-LightGBM-(GridSearchCV)-5.3.5"><span class="toc-item-num">5.3.5&nbsp;&nbsp;</span>Modelo LightGBM (GridSearchCV)</a></span></li></ul></li></ul></li><li><span><a href="#Comparación-de-cada-modelo" data-toc-modified-id="Comparación-de-cada-modelo-6"><span class="toc-item-num">6&nbsp;&nbsp;</span>Comparación de cada modelo</a></span></li><li><span><a href="#Conclusión" data-toc-modified-id="Conclusión-7"><span class="toc-item-num">7&nbsp;&nbsp;</span>Conclusión</a></span></li></ul></div>

## Descripción de los datos

Los datos se almacenan en el archivo `taxi.csv`
El número de pedidos está en la columna `num_orders`.

## Librerias usadas

- pandas
- matplotlib.pyplot
- numpy
- statsmodels
- sklearn
- lightgbm

# Conclusión

Finalmente, tras la busqueda de los mejores hiperparamentros, el modelo LightGBM con ` num_leaves=10,learning_rate= 0.25, n_estimators=200` cumplió con los requerimientos del solicitante(RMSE<48 con un RMSE de 43.8.