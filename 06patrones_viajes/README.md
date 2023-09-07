# Descripción del Proyecto
Somos un analista que trabaja para Zuber, una nueva empresa de viajes compartidos que se está lanzando en Chicago. La tarea es encontrar patrones en la información disponible. Necesitamos comprender las preferencias de los pasajeros y el impacto de los factores externos en los viajes.  

Además, se probará la veracidad de la siguiente hipótesis:
"La duración promedio de los viajes desde el Loop hasta el Aeropuerto Internacional O'Hare cambia los sábados lluviosos".


<h1>Tabla de Contenidos<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><span><a href="#Inicialización" data-toc-modified-id="Inicialización-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>Inicialización</a></span></li><li><span><a href="#Cargar-los-datos" data-toc-modified-id="Cargar-los-datos-2"><span class="toc-item-num">2&nbsp;&nbsp;</span>Cargar los datos</a></span></li><li><span><a href="#Revisión-de-los-datos-y-corregimos-de-ser-necesario" data-toc-modified-id="Revisión-de-los-datos-y-corregimos-de-ser-necesario-3"><span class="toc-item-num">3&nbsp;&nbsp;</span>Revisión de los datos y corregimos de ser necesario</a></span></li><li><span><a href="#Revisión-de-rangos" data-toc-modified-id="Revisión-de-rangos-4"><span class="toc-item-num">4&nbsp;&nbsp;</span>Revisión de rangos</a></span></li><li><span><a href="#Enriquecer-datos" data-toc-modified-id="Enriquecer-datos-5"><span class="toc-item-num">5&nbsp;&nbsp;</span>Enriquecer datos</a></span></li><li><span><a href="#Analisis-de-datos" data-toc-modified-id="Analisis-de-datos-6"><span class="toc-item-num">6&nbsp;&nbsp;</span>Analisis de datos</a></span><ul class="toc-item"><li><span><a href="#Principales-compañias" data-toc-modified-id="Principales-compañias-6.1"><span class="toc-item-num">6.1&nbsp;&nbsp;</span>Principales compañias</a></span></li><li><span><a href="#Principales-barrios" data-toc-modified-id="Principales-barrios-6.2"><span class="toc-item-num">6.2&nbsp;&nbsp;</span>Principales barrios</a></span></li></ul></li><li><span><a href="#Gráficos" data-toc-modified-id="Gráficos-7"><span class="toc-item-num">7&nbsp;&nbsp;</span>Gráficos</a></span><ul class="toc-item"><li><span><a href="#Grafico-de-principales-compañias" data-toc-modified-id="Grafico-de-principales-compañias-7.1"><span class="toc-item-num">7.1&nbsp;&nbsp;</span>Grafico de principales compañias</a></span></li><li><span><a href="#Graficamos-los-principales-barrios" data-toc-modified-id="Graficamos-los-principales-barrios-7.2"><span class="toc-item-num">7.2&nbsp;&nbsp;</span>Graficamos los principales barrios</a></span></li></ul></li><li><span><a href="#Hipótesis" data-toc-modified-id="Hipótesis-8"><span class="toc-item-num">8&nbsp;&nbsp;</span>Hipótesis</a></span><ul class="toc-item"><li><span><a href="#Test-de-Shapiro" data-toc-modified-id="Test-de-Shapiro-8.1"><span class="toc-item-num">8.1&nbsp;&nbsp;</span>Test de Shapiro</a></span></li><li><span><a href="#Test-de-Levene" data-toc-modified-id="Test-de-Levene-8.2"><span class="toc-item-num">8.2&nbsp;&nbsp;</span>Test de Levene</a></span></li><li><span><a href="#Verificacion-de-hipotesis" data-toc-modified-id="Verificacion-de-hipotesis-8.3"><span class="toc-item-num">8.3&nbsp;&nbsp;</span>Verificacion de hipotesis</a></span></li></ul></li><li><span><a href="#Conclusiones" data-toc-modified-id="Conclusiones-9"><span class="toc-item-num">9&nbsp;&nbsp;</span>Conclusiones</a></span></li></ul></div>

## Descripción de los datos

`project_sql_result_01.csv` contiene los siguientes datos:
- company_name: nombre de la empresa de taxis
- trips_amount: el número de viajes de cada compañía de taxis el 15 y 16 de noviembre de 2017.

`project_sql_result_04.csv` contiene los siguientes datos:
- dropoff_location_name: barrios de Chicago donde finalizaron los viajes
- average_trips: el promedio de viajes que terminaron en cada barrio en noviembre de 2017.

`project_sql_result_07.csv` Contiene datos sobre viajes desde el Loop hasta el Aeropuerto Internacional O'Hare. 
- start_ts: fecha y hora de la recogida
- weather_conditions: condiciones climáticas en el momento en el que comenzó el viaje
- duration_seconds: duración del viaje en segundos


## Librerias usadas

- pandas
- matplotlib.pyplot
- scipy

## Conclusiones

* El mes de noviembre hubo 4 barrios en donde los viajes terminaron mas frecuentemente. Estos fueron `Loop`,`River North`,`Streeterville` y`West Loop`.
* La empresa mas popular con diferencia es Flash Cab.
* La duración promedio de los viajes desde el Loop hasta el Aeropuerto Internacional O'Hare cambia los sábados lluviosos