# Descripción del Proyecto
Los clientes de Beta Bank se están yendo, cada mes, poco a poco. Los banqueros descubrieron que es más barato salvar a los clientes existentes que atraer nuevos.
Necesitamos predecir si un cliente dejará el banco pronto. Tenemos los datos sobre el comportamiento pasado de los clientes y la terminación de contratos con el banco.
Crearemos un modelo con el máximo valor F1 posible. Para aprobar la revisión, necesitamos un valor F1 de al menos 0.59.  Verificaremos F1 para el conjunto de prueba.
Además, mediremos la métrica AUC-ROC y la compararemos con el valor F1.

<h1>Tabla de contenidos<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><span><a href="#Inicialización" data-toc-modified-id="Inicialización-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>Inicialización</a></span></li><li><span><a href="#Cargar-los-datos" data-toc-modified-id="Cargar-los-datos-2"><span class="toc-item-num">2&nbsp;&nbsp;</span>Cargar los datos</a></span></li><li><span><a href="#Revisión-y-corrección-de-datos" data-toc-modified-id="Revisión-y-corrección-de-datos-3"><span class="toc-item-num">3&nbsp;&nbsp;</span>Revisión y corrección de datos</a></span></li><li><span><a href="#Buscando-el-mejor-modelo" data-toc-modified-id="Buscando-el-mejor-modelo-4"><span class="toc-item-num">4&nbsp;&nbsp;</span>Buscando el mejor modelo</a></span><ul class="toc-item"><li><span><a href="#Configurando-el-set-de-entrenamiento-y-validación" data-toc-modified-id="Configurando-el-set-de-entrenamiento-y-validación-4.1"><span class="toc-item-num">4.1&nbsp;&nbsp;</span>Configurando el set de entrenamiento y validación</a></span></li><li><span><a href="#Modelo-de-Regresión-logistica" data-toc-modified-id="Modelo-de-Regresión-logistica-4.2"><span class="toc-item-num">4.2&nbsp;&nbsp;</span>Modelo de Regresión logistica</a></span></li><li><span><a href="#Desequilibrio-de-clases" data-toc-modified-id="Desequilibrio-de-clases-4.3"><span class="toc-item-num">4.3&nbsp;&nbsp;</span>Desequilibrio de clases</a></span></li><li><span><a href="#Modelo-de-Arbol-de-decisión-(entrenado-con-datos-balanceados)" data-toc-modified-id="Modelo-de-Arbol-de-decisión-(entrenado-con-datos-balanceados)-4.4"><span class="toc-item-num">4.4&nbsp;&nbsp;</span>Modelo de Arbol de decisión (entrenado con datos balanceados)</a></span></li><li><span><a href="#Modelo-de-Bosques-aleatorios-(entrenado-con-datos-balanceados)" data-toc-modified-id="Modelo-de-Bosques-aleatorios-(entrenado-con-datos-balanceados)-4.5"><span class="toc-item-num">4.5&nbsp;&nbsp;</span>Modelo de Bosques aleatorios (entrenado con datos balanceados)</a></span></li></ul></li><li><span><a href="#Metrica-AUC-ROC" data-toc-modified-id="Metrica-AUC-ROC-5"><span class="toc-item-num">5&nbsp;&nbsp;</span>Metrica AUC-ROC</a></span></li><li><span><a href="#Conclusión" data-toc-modified-id="Conclusión-6"><span class="toc-item-num">6&nbsp;&nbsp;</span>Conclusión</a></span></li></ul></div>


## Descripción de los datos

**Características**  

`RowNumber`: índice de cadena de datos  
`CustomerId`: identificador de cliente único  
`Surname`: apellido  
`CreditScore`: valor de crédito  
`Geography`: país de residencia  
`Gender`: sexo  
`Age`: edad  
`Tenure`: período durante el cual ha madurado el depósito a plazo fijo de un cliente (años)  
`Balance`: saldo de la cuenta  
`NumOfProducts`: número de productos bancarios utilizados por el cliente  
`HasCrCard`: el cliente tiene una tarjeta de crédito (1 - sí; 0 - no)  
`IsActiveMember`: actividad del cliente (1 - sí; 0 - no)  
`EstimatedSalary`: salario estimado  

**Objetivo**  

`Exited`: El cliente se ha ido (1 - sí; 0 - no)

## Librerias usadas

- pandas
- matplotlib.pyplot
- sklearn

# Conclusión
El modelo que fue capaz de cumplir con los requerimentos de la empresa fue el **Modelo de bosques aleatorios con una profundidad de 4 y 13 estimadores.** Sin embargo, para entrenar este modelo, fue necesario primero balancear los datos de entrenamiento, dado que los datos proporcionados contenian porporcionalmente muy pocas filas de información de clientes que habian abandonado con respecto a la data general. Para esto, se aplicaron tecnicas de submuestreo y sobremuestro. Finalmente, analizando la curva ROC y la metrica AUC_ROC, nos aseguramos que el modelo obtenido fue un modelo de calidad.