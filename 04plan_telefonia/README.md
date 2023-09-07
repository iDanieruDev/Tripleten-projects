# ¿Cuál es un mejor plan de telefonía?

Trabajamos como analista para el operador de telecomunicaciones Megaline. La empresa ofrece a sus clientes dos tarifas de prepago, Surf y Ultimate. El departamento comercial quiere saber cuál de los planes genera más ingresos para poder ajustar el presupuesto de publicidad.

Vamos a realizar un análisis preliminar de las tarifas basado en una selección de clientes relativamente pequeña. Tenemos los datos de 500 clientes de Megaline: quiénes son los clientes, de dónde son, qué tarifa usan, así como la cantidad de llamadas que hicieron y los mensajes de texto que enviaron en 2018. Nuestro trabajo es analizar el comportamiento de los clientes y determinar qué tarifa de prepago genera más ingresos.

<h1>Tabla de contenidos<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><span><a href="#Inicialización" data-toc-modified-id="Inicialización-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>Inicialización</a></span></li><li><span><a href="#Cargar-los-datos" data-toc-modified-id="Cargar-los-datos-2"><span class="toc-item-num">2&nbsp;&nbsp;</span>Cargar los datos</a></span></li><li><span><a href="#Preparar-los-datos" data-toc-modified-id="Preparar-los-datos-3"><span class="toc-item-num">3&nbsp;&nbsp;</span>Preparar los datos</a></span></li><li><span><a href="#Planes" data-toc-modified-id="Planes-4"><span class="toc-item-num">4&nbsp;&nbsp;</span>Planes</a></span></li><li><span><a href="#Usuarios" data-toc-modified-id="Usuarios-5"><span class="toc-item-num">5&nbsp;&nbsp;</span>Usuarios</a></span><ul class="toc-item"><li><span><a href="#Corregir-datos" data-toc-modified-id="Corregir-datos-5.1"><span class="toc-item-num">5.1&nbsp;&nbsp;</span>Corregir datos</a></span></li><li><span><a href="#Enriquecer-datos" data-toc-modified-id="Enriquecer-datos-5.2"><span class="toc-item-num">5.2&nbsp;&nbsp;</span>Enriquecer datos</a></span></li></ul></li><li><span><a href="#Llamadas" data-toc-modified-id="Llamadas-6"><span class="toc-item-num">6&nbsp;&nbsp;</span>Llamadas</a></span><ul class="toc-item"><li><span><a href="#Corregir-datos" data-toc-modified-id="Corregir-datos-6.1"><span class="toc-item-num">6.1&nbsp;&nbsp;</span>Corregir datos</a></span></li><li><span><a href="#Enriquecer-datos" data-toc-modified-id="Enriquecer-datos-6.2"><span class="toc-item-num">6.2&nbsp;&nbsp;</span>Enriquecer datos</a></span></li></ul></li><li><span><a href="#Mensajes" data-toc-modified-id="Mensajes-7"><span class="toc-item-num">7&nbsp;&nbsp;</span>Mensajes</a></span><ul class="toc-item"><li><span><a href="#Corregir-datos" data-toc-modified-id="Corregir-datos-7.1"><span class="toc-item-num">7.1&nbsp;&nbsp;</span>Corregir datos</a></span></li><li><span><a href="#Enriquecer-datos" data-toc-modified-id="Enriquecer-datos-7.2"><span class="toc-item-num">7.2&nbsp;&nbsp;</span>Enriquecer datos</a></span></li></ul></li><li><span><a href="#Internet" data-toc-modified-id="Internet-8"><span class="toc-item-num">8&nbsp;&nbsp;</span>Internet</a></span><ul class="toc-item"><li><span><a href="#Corregir-datos" data-toc-modified-id="Corregir-datos-8.1"><span class="toc-item-num">8.1&nbsp;&nbsp;</span>Corregir datos</a></span></li><li><span><a href="#Enriquecer-datos" data-toc-modified-id="Enriquecer-datos-8.2"><span class="toc-item-num">8.2&nbsp;&nbsp;</span>Enriquecer datos</a></span></li></ul></li><li><span><a href="#Estudiamos-nuevamente-las-condiciones-del-plan" data-toc-modified-id="Estudiamos-nuevamente-las-condiciones-del-plan-9"><span class="toc-item-num">9&nbsp;&nbsp;</span>Estudiamos nuevamente las condiciones del plan</a></span></li><li><span><a href="#Agregamos-datos-por-usuario" data-toc-modified-id="Agregamos-datos-por-usuario-10"><span class="toc-item-num">10&nbsp;&nbsp;</span>Agregamos datos por usuario</a></span></li><li><span><a href="#Calculo-de-ingreso-mensual-por-usuario" data-toc-modified-id="Calculo-de-ingreso-mensual-por-usuario-11"><span class="toc-item-num">11&nbsp;&nbsp;</span>Calculo de ingreso mensual por usuario</a></span></li><li><span><a href="#Estudiamos-el-comportamiento-del-usuario" data-toc-modified-id="Estudiamos-el-comportamiento-del-usuario-12"><span class="toc-item-num">12&nbsp;&nbsp;</span>Estudiamos el comportamiento del usuario</a></span><ul class="toc-item"><li><span><a href="#Llamadas" data-toc-modified-id="Llamadas-12.1"><span class="toc-item-num">12.1&nbsp;&nbsp;</span>Llamadas</a></span></li><li><span><a href="#Mensajes" data-toc-modified-id="Mensajes-12.2"><span class="toc-item-num">12.2&nbsp;&nbsp;</span>Mensajes</a></span></li><li><span><a href="#Internet" data-toc-modified-id="Internet-12.3"><span class="toc-item-num">12.3&nbsp;&nbsp;</span>Internet</a></span></li></ul></li><li><span><a href="#Ingreso" data-toc-modified-id="Ingreso-13"><span class="toc-item-num">13&nbsp;&nbsp;</span>Ingreso</a></span></li><li><span><a href="#Probamos-las-hipótesis-estadísticas." data-toc-modified-id="Probamos-las-hipótesis-estadísticas.-14"><span class="toc-item-num">14&nbsp;&nbsp;</span>Probamos las hipótesis estadísticas.</a></span></li><li><span><a href="#Conclusión-general" data-toc-modified-id="Conclusión-general-15"><span class="toc-item-num">15&nbsp;&nbsp;</span>Conclusión general</a></span></li></ul></div>

## Descripción de los datos

Dataframe `users`:

- *user_id* — identificador unico de usuario
- *first_name* — nombre
- *last_name* — apellido
- *age* — edad (años)
- *reg_date* — fecha de suscripción (dd, mm, yy)
- *churn_date* — fecha en que se dejo de usar el servicio
- *city* — ciudad de residencia
- *plan* — nombre del plan

Dataframe `calls`:

- *id* — identificador unico de llamada
- *call_date* — fecha llamada
- *duration* — duracion llamada (minutos)
- *user_id* — identificador de usuario que hace la llamada

Dataframe `messages`:

- *id* — identificador unico de mensaje
- *message_date* — fecha de mensaje
- *user_id* — identificador de usuario que envia el mensaje

Dataframe `internet`:

- *id* — identificador unico de sesión
- *mb_used* — volumen de datos gastados (megabytes)
- *session_date* — fecha de sesión
- *user_id* — identificador de usuario

Dataframe `plans`:

- *plan_name* — nombre del plan
- *usd_monthly_fee* — costo mensual del plan (USD)
- *minutes_included* — minutos mensuales
- *messages_included* — cantidad de mensajes mensuales
- *mb_per_month_included* — volumen de datos mensuales (megabytes)
- *usd_per_minute* — precio por minutos extras (USD)
- *usd_per_message* — precio por mensajes adicionales
- *usd_per_gb* — precio por gigabytes extra (1 GB = 1024 megabytes)

## Librerias usadas

- pandas
- matplotlib.pyplot
- numpy
- math
- scipy

## Conclusión general

***- Vimos que al comienzo del año hubo muy pocos usuarios con planes contrados y a medida que va avanzando el año, mas usuarios se fueron sumando. En el mes de Enero hubo aproximadamente solo 10 usuarios, mientras que en Diciembre, entre los dos planes hubo mas de 400 usuarios.***

***LLAMADAS***   

-El plan "surf" fue contratado por mas personas, debido probablemente a que es mas economico.

-Los promedios de la duracion total de llamadas mensuales para ambos planes 435 minutos.

-La mayoria de las llamadas mensuales se encuentran alrededor de los 500 minutos, y solo unos poco usuarios atipicos hablar mas de 1000 minutos al mes en ambos planes.
  
  
  
***MENSAJES***   

-Los usuarios con el plan "Ultimate", suelen enviar promedio mas por mensajes de texto que los usuarios con el plan "Surf", en promedio, unos 7 mensajes mas al mes

-Para ambos planes, un porcentaje considerable de usuarios envian menos de 10 mensajes al mes

-Los usuarios del plan Surf suelen enviar entre 0 y 100 mensajes y solo un pequeño numero usuarios atipicos que envian entre 100 y 250 mensajes.

-Los usuarios del plan Ultimate, suelen enviar entre 0 y 140 mensajes y solo un pequeño numero de usuarios atipicos envian mas que esta cantidad.

***INTERNET***  

-Los usuarios del plan Ultimate, en promedio, suelen consumir 800 mb mas que los usuarios del plan Surf

Los usuario de Surf suelen controlarse y no ocupar tantos datos como los usuarios de Ultimate

Para el plan surf hubo usuario que consumio mas de 70.000 mb en un mes y sube levemente la media de ese grupo

La mediana para ambos planes ronda los 16.800 mb. pero la media para el plan ultimate es levemente mas alta

***INGRESOS***  

-En promedio, el plan Ultimate, genera mas 12 USD app mas ingresos que el plan Surf

-Los usuarios del plan Ultimate generan en promedio mas ingresos que los que tienen el plan Surf, PERO los usuarios del plan Surf generan mas ingresos en general. Esto es debido a que durante el periodo analizado, hubo significativamente mas usuarios con el plan Surf que el Ultimate. Por consecuencia, a pesar de que independientemente este plan genera menos ingresos, al ser el mas contratado, es el que genero mas ingresos para la compañia durante el año 2018***

-El rango de ingresos por usuario con el plan Surf van entre los 20 y los 170 USD.

- Los usuarios del plan Ultimate, tipicamente solo pagan los 70 USD del plan y solo en casos atipicos terminan pagando mas

***HIPOTESIS EVALUADAS***

**Hipotesis de ingresos**  
Nuestro cliente nos solicitó evaluar si es que existen diferencias entre los ingresos del plan Surf y los ingresos del plan Ultimate.

Se concluye que el **ingreso mensual de los usuarios es diferente entre los planes Surf y Ultimate**

**Hipotesis de ingresos de las región de New York vs el resto de regiones**  
Nuestro cliente nos solicita evaluar si es que existen diferencias entre los ingresos promedio de los usuarios en el área de estados Nueva York-Nueva Jersey al de los usuarios de otras regiones.

Se concluye que:  

-El ingreso promedio mensual (Surf) entre las regiones de NY-NJ-PA y otras regiones es diferente

-El ingreso promedio mensual (Ultimate) entre las regiones de NY-NJ-PA y otras regiones es la misma

-El ingreso promedio mensual considerando ambos planes, entre las regiones de NY-NJ-PA y otras regiones es la misma