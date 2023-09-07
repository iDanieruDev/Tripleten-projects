# Preferencia Musicales
En este proyecto, compararemos las preferencias musicales de las ciudades de Springfield y Shelbyville. Estudiaremos datos reales para probar tres hipótesis  y compararemos el comportamiento del usuario de esas dos ciudades.  

Hipótesis: 
1. La actividad de los usuarios difiere según el día de la semana y dependiendo de la ciudad. 
2. Los lunes por la mañana, los habitantes de Springfield y Shelbyville escuchan diferentes géneros. Lo mismo ocurre con los viernes por la noche. 
3. Los oyentes de Springfield y Shelbyville tienen preferencias distintas. En Springfield prefieren el pop mientras que en Shelbyville hay más aficionados al rap.

## Data

De acuerdo con la documentación:
- `'userID'` — identificador del usuario
- `'Track'` — título de la pista
- `'artist'` — nombre del artista
- `'genre'` — género
- `'City'` — ciudad del usuario
- `'time'` — el periodo de tiempo exacto en que se reprodujo la pista
- `'Day'` — día de la semana

<h1>Tabla de contenidos<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><span><a href="#Data" data-toc-modified-id="Data-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>Data</a></span></li><li><span><a href="#Librerias-usadas" data-toc-modified-id="Librerias-usadas-2"><span class="toc-item-num">2&nbsp;&nbsp;</span>Librerias usadas</a></span></li><li><span><a href="#Objetivo" data-toc-modified-id="Objetivo-3"><span class="toc-item-num">3&nbsp;&nbsp;</span>Objetivo</a></span></li><li><span><a href="#Etapas" data-toc-modified-id="Etapas-4"><span class="toc-item-num">4&nbsp;&nbsp;</span>Etapas</a></span></li><li><span><a href="#Etapa-1.-Descripción-de-los-datos" data-toc-modified-id="Etapa-1.-Descripción-de-los-datos-5"><span class="toc-item-num">5&nbsp;&nbsp;</span>Etapa 1. Descripción de los datos</a></span><ul class="toc-item"><li><span><a href="#Conclusiones-iniciales" data-toc-modified-id="Conclusiones-iniciales-5.1"><span class="toc-item-num">5.1&nbsp;&nbsp;</span>Conclusiones iniciales</a></span></li></ul></li><li><span><a href="#Etapa-2.-Preprocesamiento-de-datos" data-toc-modified-id="Etapa-2.-Preprocesamiento-de-datos-6"><span class="toc-item-num">6&nbsp;&nbsp;</span>Etapa 2. Preprocesamiento de datos</a></span><ul class="toc-item"><li><span><a href="#Estilo-del-encabezado" data-toc-modified-id="Estilo-del-encabezado-6.1"><span class="toc-item-num">6.1&nbsp;&nbsp;</span>Estilo del encabezado</a></span></li><li><span><a href="#Valores-ausentes" data-toc-modified-id="Valores-ausentes-6.2"><span class="toc-item-num">6.2&nbsp;&nbsp;</span>Valores ausentes</a></span></li><li><span><a href="#Duplicados" data-toc-modified-id="Duplicados-6.3"><span class="toc-item-num">6.3&nbsp;&nbsp;</span>Duplicados</a></span></li><li><span><a href="#Conclusiones-" data-toc-modified-id="Conclusiones--6.4"><span class="toc-item-num">6.4&nbsp;&nbsp;</span>Conclusiones <a id="data_preprocessing_conclusions"></a></a></span></li></ul></li><li><span><a href="#Etapa-3.-Prueba-de-hipótesis-" data-toc-modified-id="Etapa-3.-Prueba-de-hipótesis--7"><span class="toc-item-num">7&nbsp;&nbsp;</span>Etapa 3. Prueba de hipótesis <a id="hypotheses"></a></a></span><ul class="toc-item"><li><span><a href="#Hipótesis-1:-comparar-el-comportamiento-del-usuario-en-las-dos-ciudades-" data-toc-modified-id="Hipótesis-1:-comparar-el-comportamiento-del-usuario-en-las-dos-ciudades--7.1"><span class="toc-item-num">7.1&nbsp;&nbsp;</span>Hipótesis 1: comparar el comportamiento del usuario en las dos ciudades <a id="activity"></a></a></span></li><li><span><a href="#Hipótesis-2:-música-al-principio-y-al-final-de-la-semana-" data-toc-modified-id="Hipótesis-2:-música-al-principio-y-al-final-de-la-semana--7.2"><span class="toc-item-num">7.2&nbsp;&nbsp;</span>Hipótesis 2: música al principio y al final de la semana <a id="week"></a></a></span></li><li><span><a href="#Hipótesis-3:-preferencias-de-género-en-Springfield-y-Shelbyville-" data-toc-modified-id="Hipótesis-3:-preferencias-de-género-en-Springfield-y-Shelbyville--7.3"><span class="toc-item-num">7.3&nbsp;&nbsp;</span>Hipótesis 3: preferencias de género en Springfield y Shelbyville <a id="genre"></a></a></span></li></ul></li></ul></div>



## Librerias usadas

- pandas


# Conclusiones

Hemos probado las siguientes tres hipótesis:

1. La actividad de los usuarios difiere dependiendo del día de la semana y de las distintas ciudades. 
2. Los lunes por la mañana los residentes de Springfield y Shelbyville escuchan géneros distintos. Lo mismo ocurre con los viernes por la noche.
3. Los oyentes de Springfield y Shelbyville tienen distintas preferencias. En ambas ciudades, Springfield y Shelbyville, se prefiere el pop.

Tras analizar los datos, concluimos:

1. La actividad del usuario en Springfield y Shelbyville depende del día de la semana aunque las ciudades varían de diferentes formas. 

**La primera hipótesis ha sido aceptada completamente.**

2. Las preferencias musicales no varían significativamente en el transcurso de la semana en Springfield y Shelbyville. Podemos observar pequeñas diferencias en el orden los lunes, pero:
* En Springfield y Shelbyville la gente lo que más escucha es la música pop.

Así que **no podemos aceptar la segunda hipótesis**. También debemos tener en cuenta que el resultado podría haber sido diferente si no fuera por los valores ausentes.

3. Resulta que las preferencias musicales de los usuarios de Springfield y Shelbyville son bastante parecidas.

**La tercera hipótesis es rechazada**. Si hay alguna diferencia en las preferencias no se puede observar en los datos.