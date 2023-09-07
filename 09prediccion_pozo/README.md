# Descripción del Proyecto
Trabajamos para la compañía minera OilyGiant. Nuestra tarea es encontrar el mejor lugar para un nuevo pozo.  
Para esto realizaremos los siguientes pasos:  
- Recolectar los parámetros del pozo de petróleo en la región seleccionada: calidad del petróleo y volumen de reservas;
- Construir un modelo para predecir el volumen de reservas en los nuevos pozos;
- Seleccionar los pozos de petróleo con los valores estimados más altos;
- Eligir la región con el mayor beneficio total para los pozos de petróleo seleccionados.

Tenemos datos sobre muestras de crudo de tres regiones. Ya se conocen los parámetros de cada pozo petrolero de la región. Crearé un modelo que ayude a elegir la región con el mayor margen de beneficio. Analizaré los beneficios y riesgos potenciales utilizando la técnica bootstrapping.

<h1>Tabla de contenidos<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><span><a href="#Inicialización" data-toc-modified-id="Inicialización-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>Inicialización</a></span></li><li><span><a href="#Cargar-los-datos" data-toc-modified-id="Cargar-los-datos-2"><span class="toc-item-num">2&nbsp;&nbsp;</span>Cargar los datos</a></span></li><li><span><a href="#Entrenamiento-de-modelos" data-toc-modified-id="Entrenamiento-de-modelos-3"><span class="toc-item-num">3&nbsp;&nbsp;</span>Entrenamiento de modelos</a></span></li><li><span><a href="#Presupuesto-y-volumenes-promedio" data-toc-modified-id="Presupuesto-y-volumenes-promedio-4"><span class="toc-item-num">4&nbsp;&nbsp;</span>Presupuesto y volumenes promedio</a></span></li><li><span><a href="#Cálculo-de-beneficios" data-toc-modified-id="Cálculo-de-beneficios-5"><span class="toc-item-num">5&nbsp;&nbsp;</span>Cálculo de beneficios</a></span></li><li><span><a href="#Bootstrapping" data-toc-modified-id="Bootstrapping-6"><span class="toc-item-num">6&nbsp;&nbsp;</span>Bootstrapping</a></span></li><li><span><a href="#Conclusión" data-toc-modified-id="Conclusión-7"><span class="toc-item-num">7&nbsp;&nbsp;</span>Conclusión</a></span></li></ul></div>

## Descripción de los datos
Los datos de exploración geológica de las tres regiones se almacenan en archivos  

`geo_data_0.csv`  
`geo_data_1.csv`  
`geo_data_2.csv`  

Donde:  
*id*: identificador único de pozo de petróleo  
*f0, f1, f2*: tres características de los puntos  
*product*: volumen de reservas en el pozo de petróleo (miles de barriles)  

## Librerias usadas

- pandas
- matplotlib.pyplot
- numpy
- sklearn

# Conclusión
Las regiones 0 y 2 en promedio tienen mas volumen de yacimientos, sin embargo, la capacidad de los modelos para predecir con certeza el volumen de los yacimientos en estas regiones es menor a la prediciones de la región 2.
Con esto en mente, y luego de las pruebas mostradas anteriormente, a pesar de que la región 1 aparentemente tiene menos yacimientos, el poder predecir con mayor certeza el volumen de los yacimientos disminuye la posibilidad de elegir explotar un yacimiento con menos volumen del esperado y por consecuencia, se máximizan los beneficios.  
**Para la región 1, en el limite inferior de confianza de 95% (el peor de los casos), con una probabilidad de un 2.5% de riesgo, las ganancias mínimas seguiran siendo mayores que la inversión inicial. Además, el riesgo de que la inversión resulte en perdidas es del 1%, riesgo mucho menor si lo comparamos con el 6% de las otras regiones, es por esto que mi recomedación es realizar estudios de 500 nuevos puntos en la región 1 y luego elegir los mejores 200 usando el modelo confeccionado en este proyecto.**