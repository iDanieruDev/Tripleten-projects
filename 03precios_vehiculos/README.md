# ¿Qué factores influyen en el precio de vehiculo?

Somos analistas de una empresa de anuncios. Cientos de anuncios gratuitos de vehículos se publican en el sitio web cada día. Necesitamos estudiar los datos recopilados durante los últimos años y determinar qué factores influyen en el precio de un vehículo.

<h1>Tabla de contenidos<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><span><a href="#Inicialización" data-toc-modified-id="Inicialización-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>Inicialización</a></span><ul class="toc-item"><li><span><a href="#Carga-de-datos" data-toc-modified-id="Carga-de-datos-1.1"><span class="toc-item-num">1.1&nbsp;&nbsp;</span>Carga de datos</a></span></li><li><span><a href="#Explorando-datos-iniciales" data-toc-modified-id="Explorando-datos-iniciales-1.2"><span class="toc-item-num">1.2&nbsp;&nbsp;</span>Explorando datos iniciales</a></span></li><li><span><a href="#Conclusiones-y-siguientes-pasos" data-toc-modified-id="Conclusiones-y-siguientes-pasos-1.3"><span class="toc-item-num">1.3&nbsp;&nbsp;</span>Conclusiones y siguientes pasos</a></span></li></ul></li><li><span><a href="#Tratando-valores-ausentes" data-toc-modified-id="Tratando-valores-ausentes-2"><span class="toc-item-num">2&nbsp;&nbsp;</span>Tratando valores ausentes</a></span></li><li><span><a href="#Corregir-los-tipos-de-datos" data-toc-modified-id="Corregir-los-tipos-de-datos-3"><span class="toc-item-num">3&nbsp;&nbsp;</span>Corregir los tipos de datos</a></span></li><li><span><a href="#Enriquecer-datos" data-toc-modified-id="Enriquecer-datos-4"><span class="toc-item-num">4&nbsp;&nbsp;</span>Enriquecer datos</a></span></li><li><span><a href="#Comprobar-datos-limpios" data-toc-modified-id="Comprobar-datos-limpios-5"><span class="toc-item-num">5&nbsp;&nbsp;</span>Comprobar datos limpios</a></span></li><li><span><a href="#Estudiamos-parámetros-principales" data-toc-modified-id="Estudiamos-parámetros-principales-6"><span class="toc-item-num">6&nbsp;&nbsp;</span>Estudiamos parámetros principales</a></span></li><li><span><a href="#Estudiamos-y-tratamos-valores-atípicos" data-toc-modified-id="Estudiamos-y-tratamos-valores-atípicos-7"><span class="toc-item-num">7&nbsp;&nbsp;</span>Estudiamos y tratamos valores atípicos</a></span></li><li><span><a href="#Estudiamos-parámetros-principales-sin-valores-atípicos" data-toc-modified-id="Estudiamos-parámetros-principales-sin-valores-atípicos-8"><span class="toc-item-num">8&nbsp;&nbsp;</span>Estudiamos parámetros principales sin valores atípicos</a></span></li><li><span><a href="#Periodo-de-colocación-de-los-anuncios" data-toc-modified-id="Periodo-de-colocación-de-los-anuncios-9"><span class="toc-item-num">9&nbsp;&nbsp;</span>Periodo de colocación de los anuncios</a></span></li><li><span><a href="#Precio-promedio-por-cada-tipo-de-vehículo" data-toc-modified-id="Precio-promedio-por-cada-tipo-de-vehículo-10"><span class="toc-item-num">10&nbsp;&nbsp;</span>Precio promedio por cada tipo de vehículo</a></span></li><li><span><a href="#Factores-de-precio" data-toc-modified-id="Factores-de-precio-11"><span class="toc-item-num">11&nbsp;&nbsp;</span>Factores de precio</a></span></li><li><span><a href="#Resumen" data-toc-modified-id="Resumen-12"><span class="toc-item-num">12&nbsp;&nbsp;</span>Resumen</a></span></li><li><span><a href="#Conclusión-general" data-toc-modified-id="Conclusión-general-13"><span class="toc-item-num">13&nbsp;&nbsp;</span>Conclusión general</a></span></li></ul></div>


## Descripción de los datos
- `price`
- `model_year`
- `model`
- `condition`
- `cylinders`
- `fuel` — gasolina, diesel, etc.
- `odometer` — el millaje del vehículo cuando el anuncio fue publicado
- `transmission`
- `paint_color`
- `is_4wd` — si el vehículo tiene tracción a las 4 ruedas (tipo Booleano)
- `date_posted` — la fecha en la que el anuncio fue publicado
- `days_listed` — desde la publicación hasta que se elimina

## Librerias usadas

- pandas
- matplotlib.pyplot
- numpy

## Conclusión general

***Se buscaron correlaciónes entre los precios de los vehiculos con otras varibles y se dedujo lo siguiente:***  
  
***-Existe una fuerte correlación inversa entre el precio del vehiculo y su antiguedad (-0.66).  
Mientras mas antiguo, menor el precio***  
  
***-Existe una correlación inversa entre el precio del vehiculo y su millaje (-0.45).  
Mientras mas millas, menor el precio***  

***-Existe una leve correlación directa entre el precio del vehiculo y su millaje (0.33).  
Mientras mas nuevo(5), mayor el precio*** 

***Además, como era de esperar, aparece una correlación directa entre antiguedad del vehiculo y su millaje(0.5),  una correlación inversa ente la antiguedad del vehiculo y su condición(-0.3) y una leve correlación inversa entre millaje y condición (-0,29).***  

***Mientras mas viejo, mas millas  
Mientras mas viejo, menos condición  
Mientras mas millas, menos condición*** 

***Respecto al analisis de las variables categoricas versus el precio, referente a la transmisión, no se puede concluir nada ya que los tipos de transmisión "manual" y "otros" son muy pocas. Mientras que respecto al color vs precio, se aprecia que el color que registra un valor promedio mas elevado es el `negro`, mientras que el color mas economico parece ser el `verde`.***