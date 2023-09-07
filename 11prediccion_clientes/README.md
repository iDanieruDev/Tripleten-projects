# Descripción del proyecto
La compañía de seguros Sure Tomorrow quiere resolver varias tareas con la ayuda de machine learning y nos pide evaluar:
- Tarea 1: encontrar clientes que sean similares a un cliente determinado. Esto ayudará a los agentes de la compañía con el marketing.
- Tarea 2: predecir la probabilidad de que un nuevo cliente reciba una prestación del seguro. ¿Puede un modelo de predictivo funcionar mejor que un modelo dummy?
- Tarea 3: predecir el número de prestaciones de seguro que un nuevo cliente pueda recibir utilizando un modelo de regresión lineal.
- Tarea 4: proteger los datos personales de los clientes sin afectar al modelo del ejercicio anterior. Es necesario desarrollar un algoritmo de transformación de datos que dificulte la recuperación de la información personal si los datos caen en manos equivocadas. Esto se denomina enmascaramiento u ofuscación de datos. Pero los datos deben protegerse de tal manera que no se vea afectada la calidad de los modelos de machine learning. No es necesario elegir el mejor modelo, basta con demostrar que el algoritmo funciona correctamente.

<h1>Tabla de Contenidos<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><span><a href="#Inicialización" data-toc-modified-id="Inicialización-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>Inicialización</a></span></li><li><span><a href="#Carga-de-datos" data-toc-modified-id="Carga-de-datos-2"><span class="toc-item-num">2&nbsp;&nbsp;</span>Carga de datos</a></span></li><li><span><a href="#Revisión-de-datos" data-toc-modified-id="Revisión-de-datos-3"><span class="toc-item-num">3&nbsp;&nbsp;</span>Revisión de datos</a></span></li><li><span><a href="#Análisis-exploratorio-de-datos" data-toc-modified-id="Análisis-exploratorio-de-datos-4"><span class="toc-item-num">4&nbsp;&nbsp;</span>Análisis exploratorio de datos</a></span></li><li><span><a href="#Tarea-1.-Clientes-similares" data-toc-modified-id="Tarea-1.-Clientes-similares-5"><span class="toc-item-num">5&nbsp;&nbsp;</span>Tarea 1. Clientes similares</a></span><ul class="toc-item"><li><span><a href="#Distancias-euclideanas-mas-cercanas-(datos-sin-escalar)" data-toc-modified-id="Distancias-euclideanas-mas-cercanas-(datos-sin-escalar)-5.1"><span class="toc-item-num">5.1&nbsp;&nbsp;</span>Distancias euclideanas mas cercanas (datos sin escalar)</a></span></li><li><span><a href="#Distancias-euclideanas-mas-cercanas-(datos-escalados)" data-toc-modified-id="Distancias-euclideanas-mas-cercanas-(datos-escalados)-5.2"><span class="toc-item-num">5.2&nbsp;&nbsp;</span>Distancias euclideanas mas cercanas (datos escalados)</a></span></li><li><span><a href="#Distancias-Manhattan-mas-cercanas-(datos-sin-escalar)" data-toc-modified-id="Distancias-Manhattan-mas-cercanas-(datos-sin-escalar)-5.3"><span class="toc-item-num">5.3&nbsp;&nbsp;</span>Distancias Manhattan mas cercanas (datos sin escalar)</a></span></li><li><span><a href="#Distancias-Manhattan-mas-cercanas-(datos-escalados)" data-toc-modified-id="Distancias-Manhattan-mas-cercanas-(datos-escalados)-5.4"><span class="toc-item-num">5.4&nbsp;&nbsp;</span>Distancias Manhattan mas cercanas (datos escalados)</a></span></li></ul></li><li><span><a href="#Tarea-2.-¿Es-probable-que-el-cliente-reciba-una-prestación-del-seguro?" data-toc-modified-id="Tarea-2.-¿Es-probable-que-el-cliente-reciba-una-prestación-del-seguro?-6"><span class="toc-item-num">6&nbsp;&nbsp;</span>Tarea 2. ¿Es probable que el cliente reciba una prestación del seguro?</a></span><ul class="toc-item"><li><span><a href="#Clasificador-basado-en-KNN" data-toc-modified-id="Clasificador-basado-en-KNN-6.1"><span class="toc-item-num">6.1&nbsp;&nbsp;</span>Clasificador basado en KNN</a></span></li><li><span><a href="#Clasificador-dummy" data-toc-modified-id="Clasificador-dummy-6.2"><span class="toc-item-num">6.2&nbsp;&nbsp;</span>Clasificador dummy</a></span></li></ul></li><li><span><a href="#Tarea-3.-Regresión-(con-regresión-lineal)" data-toc-modified-id="Tarea-3.-Regresión-(con-regresión-lineal)-7"><span class="toc-item-num">7&nbsp;&nbsp;</span>Tarea 3. Regresión (con regresión lineal)</a></span></li><li><span><a href="#Tarea-4.-Ofuscar-datos" data-toc-modified-id="Tarea-4.-Ofuscar-datos-8"><span class="toc-item-num">8&nbsp;&nbsp;</span>Tarea 4. Ofuscar datos</a></span><ul class="toc-item"><li><span><a href="#Prueba-de-que-la-ofuscación-de-datos-puede-funcionar-con-regresión-lineal" data-toc-modified-id="Prueba-de-que-la-ofuscación-de-datos-puede-funcionar-con-regresión-lineal-8.1"><span class="toc-item-num">8.1&nbsp;&nbsp;</span>Prueba de que la ofuscación de datos puede funcionar con regresión lineal</a></span></li><li><span><a href="#Prueba-de-regresión-lineal-con-ofuscación-de-datos" data-toc-modified-id="Prueba-de-regresión-lineal-con-ofuscación-de-datos-8.2"><span class="toc-item-num">8.2&nbsp;&nbsp;</span>Prueba de regresión lineal con ofuscación de datos</a></span></li></ul></li><li><span><a href="#Conclusiones" data-toc-modified-id="Conclusiones-9"><span class="toc-item-num">9&nbsp;&nbsp;</span>Conclusiones</a></span></li><li><span><a href="#Apéndice-A:-Escribir-fórmulas-en-los-cuadernos-de-Jupyter" data-toc-modified-id="Apéndice-A:-Escribir-fórmulas-en-los-cuadernos-de-Jupyter-10"><span class="toc-item-num">10&nbsp;&nbsp;</span>Apéndice A: Escribir fórmulas en los cuadernos de Jupyter</a></span></li><li><span><a href="#Apéndice-B:-Propiedades-de-las-matrices" data-toc-modified-id="Apéndice-B:-Propiedades-de-las-matrices-11"><span class="toc-item-num">11&nbsp;&nbsp;</span>Apéndice B: Propiedades de las matrices</a></span></li></ul></div>

## Descripción de los datos

El dataset se almacena en el archivo`insurance_us.csv`  

**Características** 
- `gender`: sexo
- `age`: edad
- `income`: salario
- `family_members`: número de familiares de la persona asegurada  

**Objetivo**
- `insurance_benefits`: número de beneficios de seguro recibidos por una persona asegurada en los últimos cinco años.


## Librerias usadas

- pandas
- numpy
- math
- seaborn
- sklearn

# Conclusiones
**Tarea 1**
- El hecho de que los datos no esten escalados afecta signficativamente al cálculo de las "k" caracteristicas mas cercanas, ya que las caracteristicas con magnitudes grandes influyen en mayor magnitud respecto a las magnitudes mas pequeñas.
- Las distancias Manhattan SIEMPRE serán un poco mas largas que las distancias euclideanas.  

**Tarea 2**  

Para el problema de clasificación binaria, como usamos el criterio de los vecinos cercanos para predecir nuestro objetivo, al igual que el punto anterior,la data escalada muestra un desempeño considerablemente superior a la data sin escalar. Esto tiene sentido, ya que las columna con valores demasiado grandes de de no ser escalados, terminan influyendo casi en la totalidad el calculo dela distancia, mientras que los valores del resto de las caracteristicas pasan a ser despreciables.

**Tarea 3**

Para el caso del modelo de regresión lineal, una vez entrenado y probado tanto con los datos sin escalar, como escalados. En base a las metricas RMSE y R2, vemos que el desempeño del modelo es identico, independientemente de si esta escalado o no.

**Tarea 4**

El modelo de regresión lineal es capaz de predecir correctamente y con la misma precisión caracteristicas normales como ofuscadas (encriptadas).