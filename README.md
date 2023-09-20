# DIAGNÓSTICO CÁNCER DE MAMAS - Proyecto De Aprendizaje Automático Para La Detección Temprana De Cáncer De Mama.

De acuerdo a informes de la Organización Mundial de la Salud (OMS) cada año se producen 1,38 millones de nuevos casos de cáncer de mamas y 458.000 muertes (IARC Globocan, 2008). El cáncer de mama es, ampliamente, la enfermedad más frecuente en las mujeres, tanto en los países desarrollados como en los países en desarrollo, donde Chile, a nivel país, presenta una tasa de diagnósticos de 1 de cada 9 mujeres con esta enfermedad. 
Dada la importancia de la enfermedad nivel país y mundial, se escogió el tema en cuestión con el objetivo de realizar un análisis exploratorio del dataset relacionado al diagnóstico del cáncer de mamas proporcionado por la Unidad de Data Science de la Universidad de Concepción para hacer esta investigación, siendo el objetivo poder predecir el diagnóstico de un tumor si es Maligno (M) o Benigno (B) a partir de un conjunto de datos sobre el análisis de una biopsia de bulto en mama. 

El dataset dispuesto cuenta con 569 muestras, 357 de ellas benignas y 212 malignas.
Cada muestra posee una identificación (“ID”), el diagnóstico (“diagnosis”) y 30 atributos relacionados a 10 características divididas en 3 tipo variable descriptiva:
1: “Mean”, 2:” Se”, 3: “Worst”. De estas se entregan la siguiente información de cada una:


1. Radius: media de las distancias desde el centro hacia puntos del perímetro.

2. Texture: desviación estándar de las intensidades en escala de grises.

3. Perimeter: contorno de biopsia.

4. Area: superficie de la biopsia.

5. Smoothness: variación local de largo de los radios.

6. Compactness:  / área 

7. Concavity: severidad de secciones cóncavas en la delineación.

8. Concave points: número de secciones cóncavas en la delineación.

9. Symmetry: simetría de la biopsia. 

10. Fractal dimension: "Paradoja de línea de Costa" 

## PARTE 1: ANÁLISIS EXPLORATORIO
A.	Limpieza Base de Datos

B.	Descripción de los Datos

C.	Análisis Gráfico (Univariables)

D.	Correlaciones entre variables

## PARTE 2: MODELO PREDICTIVO
A.	División de los datos

B.	Propuesta de Modelo

  - Regresión Logística
  - SVM
  - Random Forest
C.	Elección y Entrenamiento del Modelo

## CONCLUSIONES


PARTE 1: ANÁLISIS EXPLORATORIO

| Nombre                 | Tipo de Variable        |
|------------------------|-------------------------|
| id                     | Cuantitativa Discreta   |
| diagnosis              | Cualitativa             |
| radius_mean            | Cuantitativa Continua   |
| texture_mean           | Cuantitativa Continua   |
| perimeter_mean         | Cuantitativa Continua   |
| area_mean              | Cuantitativa Continua   |
| smoothness_mean        | Cuantitativa Continua   |
| compactness_mean       | Cuantitativa Continua   |
| concavity_mean         | Cuantitativa Continua   |
| concave points_mean    | Cuantitativa Continua   |
| symmetry_mean          | Cuantitativa Continua   |
| fractal_dimension_mean | Cuantitativa Continua   |
| radius_se              | Cuantitativa Continua   |
| texture_se             | Cuantitativa Continua   |
| perimeter_se           | Cuantitativa Continua   |
| area_se                | Cuantitativa Continua   |
| smoothness_se          | Cuantitativa Continua   |
| compactness_se         | Cuantitativa Continua   |
| concavity_se           | Cuantitativa Continua   |
| concave points_se      | Cuantitativa Continua   |
| symmetry_se            | Cuantitativa Continua   |
| fractal_dimension_se   | Cuantitativa Continua   |
| radius_worst           | Cuantitativa Continua   |
| texture_worst          | Cuantitativa Continua   |
| perimeter_worst        | Cuantitativa Continua   |
| area_worst             | Cuantitativa Continua   |
| smoothness_worst       | Cuantitativa Continua   |
| compactness_worst      | Cuantitativa Continua   |
| concavity_worst        | Cuantitativa Continua   |
| concave points_worst   | Cuantitativa Continua   |
| symmetry_worst         | Cuantitativa Continua   |
| fractal_dimension_worst| Cuantitativa Continua   |



Como primera inferencia con respecto las variables se decidió omitir la variable “ID”, la cual representa la identificación de la muestra/examen realizado, no siendo una variable continua que pueda explicar el diagnóstico de si un cáncer es benigno o maligno, ya que este es solo un registro sin presentar información descriptiva.

## A.Limpieza Base de Datos
Ya identificadas las variables y sus respectivos datos que no aportarán a la validación de la hipótesis planteada, se procedió a eliminar dos variables (“ID” y “Unnamed: 32”).

## B.Descripción de los Datos.
Ya efectuada la limpieza, tras la eliminación de datos que no aportaran al análisis, se realizó un análisis descriptivo a de las columnas indicando sus valores máximos, mínimos, cuartiles, promedios y desviación estándar.

![image](https://github.com/CetoKaiva/ConsultoriaMACCI/assets/130872798/55f3ff80-77ed-409a-9479-3f791bb4bfd1)


De la tabla anterior, fue posible detectar la siguiente información: 
- el conteo de valores es el mismo en todas las columnas (569), confirmando la inexistencia de valores nulos. 
- Por otro lado, se ratificó la cantidad de diagnósticos de cáncer benignos y malignos del total de datos se observa que el 62,7% corresponden a un diagnóstico benigno y 37,3% corresponde a un diagnóstico maligno.

![image](https://github.com/CetoKaiva/ConsultoriaMACCI/assets/130872798/82e6c2f4-1240-4067-b099-61b1551428ee)


Posteriormente, se analizó una comparación general entre los tumores Benignos y Malignos, agrupando los datos para obtener los promedios de los resultados. Se observa que hay una diferencia identificada por la columna “Delta” y su correspondiente sigo , ya que este hace referencia a la diferencia entre Benigno y Maligno.

![image](https://github.com/CetoKaiva/ConsultoriaMACCI/assets/130872798/1d7db661-d961-4eb6-95ed-7b9e8d803ba1)


De la tabla anterior, fue posible analizar que los valores promedio (media) cuando el diagnóstico es maligno, son en casi todos los indicadores son mayores que los diagnosticados como benigno, excepto en “Fractal_Dimension_mean” donde son prácticamente iguales.
Realizando un análisis entre el diagnóstico segmentado por resultado (M / B) y algunos de sus características se encuentra:

![image](https://github.com/CetoKaiva/ConsultoriaMACCI/assets/130872798/ba0447ab-3d30-4e7f-983e-f98caf62bc23)
![image](https://github.com/CetoKaiva/ConsultoriaMACCI/assets/130872798/c005c2f0-682c-4c64-938b-1fc371205d7a)




## C.Análisis Gráfico (Univariables)
A continuación, se hace una comparativa de histogramas para las diferentes variables divididas por “mean”, “Se” y “worst” para visualizar su distribución y simetría de sus respectivos valores.

![image](https://github.com/CetoKaiva/ConsultoriaMACCI/assets/130872798/13e1da9b-f2de-424c-9ef1-cae074ceee00)

De los histogramas es posible inferir:
- En su mayoría, las distribuciones son asimétricas a la derecha, por lo que presenta una curtosis mayor hacia la derecha, reflejando una mayor concentración de datos con respecto a la media. 
- La asimetría nos indica que tanta variabilidad presentan los datos.


## D.Correlaciones entre variables
A partir de los datos también se busca ver qué variables pueden explicar mejor el resultado del diagnóstico, es por esto que se hace un análisis de correlación con respecto a las variables del dataset. 
Para poder ilustrar la correlación se presenta el siguiente mapa de calor, donde la diagonal siempre presenta el valor de “1” (correspondiente al 100%) ya que evalúa la variable con sí misma, obteniendo como resultado la relación entre variables:

![image](https://github.com/CetoKaiva/ConsultoriaMACCI/assets/130872798/d440752b-263b-4d28-a703-b8c57e62f77f)


Como resultado, la matriz de correlación muestra las mayores correlaciones con colores más oscuros. 
Como resultado del análisis, se pueden observar fuera de esta diagonal principal también fuertes correlaciones cercanas a 1, sin embargo, estas se vienen refiriendo a las columnas de perímetro, área y radio, por lo que estas correlaciones no explicarían el modelo en sí para determinar si es benigno o no, más bien serían valores que son directamente dependientes entre sí, para determinar estas características en su cálculo matemático y presentan multicolinealidad , pudiendo interferir en el pronóstico del modelo a investigar. 
Las columnas que tienen su valor directamente dependiente del radio son: 
- Perimeter_mean 
- area_mean
- smoothness_mean
- compactness_mean

En base al problema de multicolinealidad que presenta, con el objetivo de eliminar variables altamente correlacionadas se procede a eliminar aquellas variables sobre 0.9.Logrando el siguiente mapa de correlación:

![image](https://github.com/CetoKaiva/ConsultoriaMACCI/assets/130872798/a9331c85-eff4-46cb-b060-dc3991624cba)


