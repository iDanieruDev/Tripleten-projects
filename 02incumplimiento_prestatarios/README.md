# Análisis del riesgo de incumplimiento de los prestatarios

El proyecto consiste en preparar un informe para la división de préstamos de un banco. Averiguaré si el estado civil y el número de hijos de un cliente tienen un impacto en el incumplimiento de pago de un préstamo. El banco ya tiene algunos datos sobre la solvencia crediticia de los clientes.

El informe se tendrá en cuenta al crear una **puntuación de crédito** para un cliente potencial. La **puntuación de crédito** se utiliza para evaluar la capacidad de un prestatario potencial para pagar su préstamo.

<h1>Tabla de contenidos<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><span><a href="#Abro-el-archivo-de-datos-y-miro-la-información-general." data-toc-modified-id="Abro-el-archivo-de-datos-y-miro-la-información-general.-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>Abro el archivo de datos y miro la información general.</a></span></li><li><span><a href="#Ejercicio-1.-Exploración-de-datos" data-toc-modified-id="Ejercicio-1.-Exploración-de-datos-2"><span class="toc-item-num">2&nbsp;&nbsp;</span>Ejercicio 1. Exploración de datos</a></span><ul class="toc-item"><li><span><a href="#Conclusión-intermedia" data-toc-modified-id="Conclusión-intermedia-2.1"><span class="toc-item-num">2.1&nbsp;&nbsp;</span>Conclusión intermedia</a></span></li><li><span><a href="#Conclusión-intermedia" data-toc-modified-id="Conclusión-intermedia-2.2"><span class="toc-item-num">2.2&nbsp;&nbsp;</span>Conclusión intermedia</a></span></li></ul></li><li><span><a href="#Transformación-de-datos" data-toc-modified-id="Transformación-de-datos-3"><span class="toc-item-num">3&nbsp;&nbsp;</span>Transformación de datos</a></span><ul class="toc-item"><li><span><a href="#Restaurando-valores-ausentes-en-total_income" data-toc-modified-id="Restaurando-valores-ausentes-en-total_income-3.1"><span class="toc-item-num">3.1&nbsp;&nbsp;</span>Restaurando valores ausentes en <code>total_income</code></a></span></li><li><span><a href="#Restaurando-valores-en-days_employed" data-toc-modified-id="Restaurando-valores-en-days_employed-3.2"><span class="toc-item-num">3.2&nbsp;&nbsp;</span>Restaurando valores en <code>days_employed</code></a></span></li></ul></li><li><span><a href="#Clasificación-de-datos" data-toc-modified-id="Clasificación-de-datos-4"><span class="toc-item-num">4&nbsp;&nbsp;</span>Clasificación de datos</a></span></li><li><span><a href="#Comprobación-de-las-hipótesis" data-toc-modified-id="Comprobación-de-las-hipótesis-5"><span class="toc-item-num">5&nbsp;&nbsp;</span>Comprobación de las hipótesis</a></span></li></ul></div>

## Descripción de los datos
- `children` - el número de hijos en la familia
- `days_employed` - experiencia laboral en días
- `dob_years` - la edad del cliente en años
- `education` - la educación del cliente
- `education_id` - identificador de educación
- `family_status` - estado civil
- `family_status_id` - identificador de estado civil
- `gender` - género del cliente
- `income_type` - tipo de empleo
- `debt` - ¿había alguna deuda en el pago de un préstamo?
- `total_income` - ingreso mensual
- `purpose` - el propósito de obtener un préstamo


## Librerias usadas

- pandas
- matplotlib.pyplot
- numpy

# Conclusión general 

***La data proporcionada para el analisis, disponia de 21524 filas, sin embargo, existian varias filas y columnas, tanto con datos nulos como con datos duplicados o incorrectos***

En resumen, de los datos se corrigio lo siguiente:

1.Se estandarizó el formato de `education` todo en minuscula y snake_case  
2.En la columna `children` habian valores de -1 y 20, se asumieron errores de tipeo. ***-1 se igualo a 1 y 20 se igualo a 2.***
3.Se corrigieron valores de `days_employed` mal escalados.
4.En `dob_years` habian 110 filas con edad de 0 años, se procede a calcular la edad estimada tomando como base los dias de experincia (`days_employed`)
5.En `gender` hay una fila con una valor XNA, la cual fue reetiquetada como "no-binario"
6.Buscamos duplicados implicitos, encontramos 71 filas(0.4%). Las borramos.  
7.Se calculó la mediana de datos no nulos de la columna `total_income` según el tipo de empleo, educación, genero y rango de edad para luego asignar según correspondiese.  
8.Se calculó la media de datos no nulos de la columna `days_employed` según el tipo de empleo, educación, genero y rango de edad para luego asignar según correspondiese.  

***Luego de todo lo anterior, nuestro conjunto de datos paso de tener 21524 filas a 21444.***

# Conclusiones finales

***1.Solo las personas sin hijos tienden a tener una menor probabilidad a endeudarse.
2.La gente soltera (unmarried) y las con union civil (civil partnership) presentan un mayor porcentaje de deuda  
3.Mientras mayor es el ingreso, menor es la probabilidad de presentar endeudamiento  
4.Las personas que solicitan un prestamo para comprar un automovil, tienen una mayor probabilidad al endeudamiento, mientras que las que lo piden para adquirir una casa, son las mas confiables.***