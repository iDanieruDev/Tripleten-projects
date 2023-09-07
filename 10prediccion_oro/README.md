# Descripción del Proyecto

El proyecto consistirá en preparar el prototipo de un modelo de machine learning para Zyfra. La empresa desarrolla soluciones de eficiencia para la industria pesada.
El modelo deberá predecir la cantidad de oro extraído del mineral de oro. Disponemos de los datos de extracción y purificación.

Los datos se almacenan en tres archivos:  
- `gold_recovery_train.csv` — el dataset de entrenamiento  
- `gold_recovery_test.csv` —el dataset de prueba  
- `gold_recovery_full.csv` — el dataset fuente  

Los datos se indexan con la fecha y la hora de adquisición (date). Los parámetros cercanos en el tiempo suelen ser similares.
Algunos parámetros no están disponibles porque fueron medidos o calculados mucho más tarde. Por eso, algunas de las características que están presentes en el conjunto de entrenamiento pueden estar ausentes en el conjunto de prueba. El conjunto de prueba tampoco contiene objetivos.
El dataset fuente contiene los conjuntos de entrenamiento y prueba con todas las características.

<h1>Tabla de Contenidos<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><span><a href="#Inicialización" data-toc-modified-id="Inicialización-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>Inicialización</a></span></li><li><span><a href="#Cargar-los-datos" data-toc-modified-id="Cargar-los-datos-2"><span class="toc-item-num">2&nbsp;&nbsp;</span>Cargar los datos</a></span><ul class="toc-item"><li><span><a href="#Dataset-de-entrenamiento-(data_train)" data-toc-modified-id="Dataset-de-entrenamiento-(data_train)-2.1"><span class="toc-item-num">2.1&nbsp;&nbsp;</span>Dataset de entrenamiento (data_train)</a></span></li><li><span><a href="#Dataset-de-prueba-(data_test)" data-toc-modified-id="Dataset-de-prueba-(data_test)-2.2"><span class="toc-item-num">2.2&nbsp;&nbsp;</span>Dataset de prueba (data_test)</a></span></li><li><span><a href="#Dataset-completo-(data_full)" data-toc-modified-id="Dataset-completo-(data_full)-2.3"><span class="toc-item-num">2.3&nbsp;&nbsp;</span>Dataset completo (data_full)</a></span></li></ul></li><li><span><a href="#Preparación-de-los-datos" data-toc-modified-id="Preparación-de-los-datos-3"><span class="toc-item-num">3&nbsp;&nbsp;</span>Preparación de los datos</a></span><ul class="toc-item"><li><span><a href="#Comprobación-del-cálculo-de-recuperación" data-toc-modified-id="Comprobación-del-cálculo-de-recuperación-3.1"><span class="toc-item-num">3.1&nbsp;&nbsp;</span>Comprobación del cálculo de recuperación</a></span></li><li><span><a href="#Analisis-del-dataset-de-prueba-(data_test)" data-toc-modified-id="Analisis-del-dataset-de-prueba-(data_test)-3.2"><span class="toc-item-num">3.2&nbsp;&nbsp;</span>Analisis del dataset de prueba (data_test)</a></span></li><li><span><a href="#Preprocesamiento-de-los-datos-de-entrenamiento-(data_train)" data-toc-modified-id="Preprocesamiento-de-los-datos-de-entrenamiento-(data_train)-3.3"><span class="toc-item-num">3.3&nbsp;&nbsp;</span>Preprocesamiento de los datos de entrenamiento (data_train)</a></span></li></ul></li><li><span><a href="#Analisis-antes-del-entrenamiento" data-toc-modified-id="Analisis-antes-del-entrenamiento-4"><span class="toc-item-num">4&nbsp;&nbsp;</span>Analisis antes del entrenamiento</a></span><ul class="toc-item"><li><span><a href="#Concentración-de-los-metales-en-cada-fase" data-toc-modified-id="Concentración-de-los-metales-en-cada-fase-4.1"><span class="toc-item-num">4.1&nbsp;&nbsp;</span>Concentración de los metales en cada fase</a></span></li><li><span><a href="#Limpieza-de-valores-anormales" data-toc-modified-id="Limpieza-de-valores-anormales-4.2"><span class="toc-item-num">4.2&nbsp;&nbsp;</span>Limpieza de valores anormales</a></span></li><li><span><a href="#Distribución-del-tamaño-de-las-particulas-de-alimentación" data-toc-modified-id="Distribución-del-tamaño-de-las-particulas-de-alimentación-4.3"><span class="toc-item-num">4.3&nbsp;&nbsp;</span>Distribución del tamaño de las particulas de alimentación</a></span></li></ul></li><li><span><a href="#Entrenamiento-de-modelos" data-toc-modified-id="Entrenamiento-de-modelos-5"><span class="toc-item-num">5&nbsp;&nbsp;</span>Entrenamiento de modelos</a></span><ul class="toc-item"><li><span><a href="#Metrica-de-evaluación-del-modelo-(sMAPE)" data-toc-modified-id="Metrica-de-evaluación-del-modelo-(sMAPE)-5.1"><span class="toc-item-num">5.1&nbsp;&nbsp;</span>Metrica de evaluación del modelo (sMAPE)</a></span></li><li><span><a href="#Entrenamiento-de-modelos" data-toc-modified-id="Entrenamiento-de-modelos-5.2"><span class="toc-item-num">5.2&nbsp;&nbsp;</span>Entrenamiento de modelos</a></span><ul class="toc-item"><li><span><a href="#Preparación-final-de-dataset-de-entrenamiento" data-toc-modified-id="Preparación-final-de-dataset-de-entrenamiento-5.2.1"><span class="toc-item-num">5.2.1&nbsp;&nbsp;</span>Preparación final de dataset de entrenamiento</a></span></li><li><span><a href="#Entrenamiento-del-modelo" data-toc-modified-id="Entrenamiento-del-modelo-5.2.2"><span class="toc-item-num">5.2.2&nbsp;&nbsp;</span>Entrenamiento del modelo</a></span></li></ul></li></ul></li><li><span><a href="#Aplicación-del-modelo-con-muestra-de-prueba" data-toc-modified-id="Aplicación-del-modelo-con-muestra-de-prueba-6"><span class="toc-item-num">6&nbsp;&nbsp;</span>Aplicación del modelo con muestra de prueba</a></span></li><li><span><a href="#Conclusion" data-toc-modified-id="Conclusion-7"><span class="toc-item-num">7&nbsp;&nbsp;</span>Conclusion</a></span></li></ul></div>


## Descripción de los datos

**Proceso tecnológico**  
- `Rougher feed` — materia prima  
- `Rougher additions (o adiciones de reactivos)` - reactivos de flotación: xantato, sulfato, depresante  
- `Xantato` — promotor o activador de la flotación  
- `Sulfato` — sulfuro de sodio para este proceso en particular  
- `Depresante` — silicato de sodio  
- `Rougher process` — flotación  
- `Rougher tails` — residuos del producto  
- `Float banks` — instalación de flotación  
- `Cleaner process` — purificación  
- `Rougher Au` — concentrado de oro rougher  
- `Final Au` — concentrado de oro final  

**Parámetros de las etapas**  
- `air amount` — volumen de aire  
- `fluid levels`  
- `feed size` — tamaño de las partículas de la alimentación  
- `feed rate`  

**Denominación de las características**  
Así es como se denominan las características:  
`[stage].[parameter_type].[parameter_name]`  

Ejemplo: `rougher.input.feed_ag`  
Valores posibles para `[stage]`:
- rougher — flotación
- primary_cleaner — purificación primaria
- secondary_cleaner — purificación secundaria
- final — características finales

Valores posibles para `[parameter_type]`:
- input — parámetros de la materia prima
- output — parámetros del producto
- state — parámetros que caracterizan el estado actual de la etapa
- calculation — características de cálculo

## Librerias usadas

- pandas
- matplotlib.pyplot
- numpy
- sklearn

# Conclusión
Luego de poner a prueba tres modelos de predicción diferentes, el modelo de arbol de decisión(DecisionTreeRegressor) fue el que mostro un mejor desempeño utilizando como hiperparaneotro max_depth=2.
**Respecto al desempeño, obtuvimos que el modelo predice la concentración de oro a la salida de la flotación con un error medio absoluto porcentual simétrico(sMAPE) de 4.046.**
