# Descripción del Proyecto
Trabajamos para la tienda online Ice que vende videojuegos por todo el mundo. Las reseñas de usuarios y expertos, los géneros, las plataformas (por ejemplo, Xbox o PlayStation) y los datos históricos sobre las ventas de juegos están disponibles en fuentes abiertas. Debemos identificar patrones que determinen si un juego tiene éxito o no. Esto nos permitirá detectar proyectos prometedores y planificar campañas publicitarias.

El dataset contiene la abreviatura ESRB. The Entertainment Software Rating Board (la Junta de clasificación de software de entretenimiento) evalúa el contenido de un juego y asigna una clasificación de edad como Adolescente o Adulto.

Lo datos proporcionados se remontan al año 2016.

## Descripción de los datos

- *Name*: Nombre de juego
- *Platform*: Plataforma del juego
- *Year_of_Release* : Año de salida
- *Genre*: Género
- *NA_sales*: Ventas en Norteamerica (en millones de USD)
- *EU_sales*: Ventas en Europa (en millones de USD)
- *JP_sales*: Ventas en Japón (en millones de USD)
- *Other_sales*: Ventas en otros paises (en millones de USD)
- *Critic_Score*: Calificación de la crítica (máximo de 100)
- *User_Score*: Calificación de los usuarios (máximo de 10)
- *Rating*: (ESRB)

## Librerias usadas

- pandas
- matplotlib.pyplot
- numpy
- math
- scipy
- warnings

# Conclusión
**Para el periodo analizado (2012-2016)**
* Las plataformas mas relevantes en relación al número de ventas fueron "PS4", "PS3", "X360", "3DS", "XOne" y "WiiU".
* Las menos relevantes fueron las plataformas "PSP", "DS" y "Wii".
* En el 2012 las plataformas mas populares eran PS3, X360, seguida de la portatil 3DS.
* En el 2016 las plataformas con mayor relevancia son PS4, XOne y 3DS.

**Ventas (2012-2016)**
* El ingreso promedio para la PS4 es de 800.000 dolares con ingresos tipicos entre 10.000 y 1.750.000 dolares app.
* El ingreso promedio la XOne es de 645.000 dolares con ingresos tipicos entre 10.000 y 1.600.000 dolares app.
* El ingreso promedio para la 3DS es de 490.000 dolares con ingresos típicos entre 10.000 y 750.000 dolares app.

**Correlaciones ventas vs/Reseñas**
* Existe una correlación directa entre la calificación de la crítica y las ventas del titulo.


**Ganancias por género (2012-2016)**
* Los géneros mas populares son Action, Shooting, Role-Playing y Sports.
* El género de un juego no siempre garantiza el exito o fracaso del mismo.

**Diferencias por región**  
*Plataformas*
* En el 2012 en Norteamerica y Europa las plataformas mas populares eran PS3, X360 y 3DS.
* En el 2016 en Norteamerica y Europa las plataformas mas populares eran PS4 y XOne.
* En Japón la plataforma mas popular en los últimos 5 años es 3DS.
* En 2016 en Japón las consolas mas populares despues de 3DS son PS4 y PSV.

*Géneros*
* En Norteamerica y Europa el género mas popular es Action, seguido por Shotter, luego Sports y Role-Playing.
* Para Norteamerica el quinto género mas popular es Misc.
* Para Europa el quinto género mas popular es Racing.
* En Japón el género Role-Playing es el mas popular, seguido del género Action.  

*Clasificacion ESRB*
* En Norteamerica y Europa los juegos populares son clasificación M (Mature). Luego E, T y E+10.
* En Japón los juegos populares son clasificación E (Everyone). Luego T, M y E+10.

**Hipotesis**
* Las calificaciones promedio de los usuarios para los juegos de las plataformas XOne y PC son similares.
* Las calificaciones promedio de los usuarios para los juegos de los géneros de Action y Sports son diferentes.