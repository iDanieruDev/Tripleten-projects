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