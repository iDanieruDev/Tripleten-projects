# Descripción del Proyecto
La compañía móvil Megaline no está satisfecha al ver que muchos de sus clientes utilizan planes heredados. Quieren desarrollar un modelo que pueda analizar el comportamiento de los clientes y recomendar uno de los nuevos planes de Megaline: Smart o Ultra.
Tenemos acceso a los datos de comportamiento de los suscriptores que ya se han cambiado a los planes nuevos (del proyecto del curso de Análisis estadístico de datos). Para esta tarea de clasificación crearemos un modelo que escoja el plan correcto.
En un proyecto anterior, ya trabajamos con esta información y ya hicimos el paso de procesar los datos, por lo que podemos saltarnos este paso y pasar directamente a la creación de nuestro modelo.

<h1>Tabla de contenidos<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><span><a href="#Inicialización" data-toc-modified-id="Inicialización-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>Inicialización</a></span></li><li><span><a href="#Cargar-los-datos" data-toc-modified-id="Cargar-los-datos-2"><span class="toc-item-num">2&nbsp;&nbsp;</span>Cargar los datos</a></span></li><li><span><a href="#Revisión-de-los-datos" data-toc-modified-id="Revisión-de-los-datos-3"><span class="toc-item-num">3&nbsp;&nbsp;</span>Revisión de los datos</a></span></li><li><span><a href="#Creación-de-modelos" data-toc-modified-id="Creación-de-modelos-4"><span class="toc-item-num">4&nbsp;&nbsp;</span>Creación de modelos</a></span><ul class="toc-item"><li><span><a href="#Segmentación-de-datos" data-toc-modified-id="Segmentación-de-datos-4.1"><span class="toc-item-num">4.1&nbsp;&nbsp;</span>Segmentación de datos</a></span></li><li><span><a href="#Entrenamiento-de-Arboles-de-decisión-(DecisionTreeClassifier)" data-toc-modified-id="Entrenamiento-de-Arboles-de-decisión-(DecisionTreeClassifier)-4.2"><span class="toc-item-num">4.2&nbsp;&nbsp;</span>Entrenamiento de Arboles de decisión (DecisionTreeClassifier)</a></span></li><li><span><a href="#Entrenamiento-de-bosques-aleatorios-(RandomForestClassifier)" data-toc-modified-id="Entrenamiento-de-bosques-aleatorios-(RandomForestClassifier)-4.3"><span class="toc-item-num">4.3&nbsp;&nbsp;</span>Entrenamiento de bosques aleatorios (RandomForestClassifier)</a></span></li><li><span><a href="#Modelo-de-Regresión-Logistica" data-toc-modified-id="Modelo-de-Regresión-Logistica-4.4"><span class="toc-item-num">4.4&nbsp;&nbsp;</span>Modelo de Regresión Logistica</a></span></li></ul></li><li><span><a href="#Calidad-de-los-distintos-modelos" data-toc-modified-id="Calidad-de-los-distintos-modelos-5"><span class="toc-item-num">5&nbsp;&nbsp;</span>Calidad de los distintos modelos</a></span></li><li><span><a href="#Probando-nuestro-modelo" data-toc-modified-id="Probando-nuestro-modelo-6"><span class="toc-item-num">6&nbsp;&nbsp;</span>Probando nuestro modelo</a></span></li><li><span><a href="#Conclusión" data-toc-modified-id="Conclusión-7"><span class="toc-item-num">7&nbsp;&nbsp;</span>Conclusión</a></span></li></ul></div>

## Descripción de los datos

- `сalls` — número de llamadas
- `minutes` — duración de la llamada (en minutos)
- `messages` — número de mensajes de texto
- `mb_used` — frafico de internet usado (MB)
- `is_ultra` — plan del mes actual (Ultra - 1, Smart - 0).

## Librerias usadas

- pandas
- matplotlib.pyplot
- sklearn

# Conclusión
De los 3 modelos entrenados, finalmente **el modelo de arbol de decision de profundidad 3 con una seed=12345 es el que mejor cumple los requerimientos de la empresa, siendo capaz de recomendar un plan para un nuevo usuario con un 77,6% de certeza.**  

Tambien vimos que un modelo, por muy preciso que aparente ser, como lo fue el caso de bosques aleatorios, puede no ser siempre el adecuado ya que esta precisión puede venir acompañada de un sobreajuste, el cual limita la capacidad del modelo de generalizar y de responder adecuadamente a información nueva que se aleje de los datos del dataset de entrenamiento.