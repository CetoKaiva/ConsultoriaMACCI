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


# PARTE 1: ANÁLISIS EXPLORATORIO

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



# PARTE 2: MODELO PREDICTIVO

## A.División de los datos:

El primer paso ahora la separación de datos , el cual se divide en 2 partes :
1.Separación de datos entre variables predictoras de los cuales el algoritmo aprenderá y la variable a predecir que seria el resultado B o M
2.Separación de los datos entre datos de entrenamiento y test, en este caso se considera un 70% de los datos para el entrenamiento del modelo y un 30% para la posterior validación del modelo, en este proceso la selección de los datos es completamente aleatoria y evita sesgos. 


## B.Propuesta de Modelo

Se consideraron 3 modelos a evaluar cual de ellos cumple con los mejores indicadores para ser elegido el modelo que se utilizara como predictor de nuevas muestras como B o M, que son : Regresión logística, SVM y Ramdom Forest tal y como lo muestra la imagen x

![image](https://github.com/CetoKaiva/ConsultoriaMACCI/assets/130872798/31c4d292-2105-4485-ab09-5af1b20d70be)

Elección de métricas de rendimiento para evaluar los modelos:
- Exactitud(Accuracy) = Con qué frecuencia el modelo clasifica correctamente
- Precisión = Precisión del modelo a la hora de clasificar casos Malignos
- Sensibilidad(Recall) = Cuan sensible es el clasificador para detectar instancias Malignas


## Regresión Logística

Realizado los análisis, se procede a definir un modelo de regresión que se adecue a nuestros datos, uno de ellos es el de regresión logística.
Este es un modelo el cual utiliza un método estadístico supervisado para predecir clases binarias, en este caso, si el cáncer es Benigno (B) o Maligno (M), cuyo resultado es de naturaleza dicotómica. Si se cumplen los supuestos y se logra convergencia, el método de predicción mediante regresión logística resulta uno de los más robusto para este tipo de casos.
Junto con lo anterior, para proponer un modelo de Regresión Logística es necesario tener en cuenta las siguientes consideraciones, y su cumplimiento, para la implementación del Modelo:
- La Variable objetivo (variable a predecir) debe ser dicotómica.
- Los predictores deben ser independientes.
- Para tener un modelo más estable los predictores deben tener una distribución normal.
- No existencia de multicolinealidad, ya que puede llevar a predicciones sesgadas. 
- Verificación de la normalidad multivariante.

El modelo ajustado mediante una regresión logística posee una exactitud del 97,66%, una precisión del 98,48% y una sensibilidad del 95,59% con las siguientes métricas obtenidas a partir de su respectiva matriz de confusión, de dicha matriz podemos concluir que :
- 102 muestras fueron catalogadas como Benignas y efectivamente lo eran, mientras que 3 muestras Benignas fueron catalogadas como Malignas.
- 65 muestras fueron catalogadas como malignas y efectivamente lo eran, mientras que una muestra que era maligna fue catalogada como beningna

![image](https://github.com/CetoKaiva/ConsultoriaMACCI/assets/130872798/c9c9ae72-87d2-4811-b12d-320c331014b5)

## SVM
SVM funciona correlacionando datos a un espacio de características de grandes dimensiones de forma que los puntos de datos se puedan categorizar, incluso si los datos no se puedan separar linealmente de otro modo.
Se detecta un separador entre las categorías y los datos se transforman de forma que el separador se puede extraer como un hiperplano. Tras ello, las características de los nuevos datos se pueden utilizar para predecir el grupo al que pertenece el nuevo registro.

Este modelo presentó una exactitud del 96,49%%, una precisión del 95,59% y una sensibilidad del 95,59%  con las siguientes métricas obtenidas a partir de su respectiva matriz de confusión.
- 100 muestras fueron catalogadas como Benignas y efectivamente lo eran, mientras que 3 muestras Benignas fueron catalogadas como Malignas.
- 65 muestras fueron catalogadas como malignas y efectivamente lo eran, mientras que 3 muestras que eran malignas fue catalogada como beningna

![image](https://github.com/CetoKaiva/ConsultoriaMACCI/assets/130872798/11f72bfe-f87e-42ce-af02-c3e0e7aaecc2)


## Random Forest
Random Forest es un modelo a Machine learning que tiene una capacidad de generalización ata para ciertos tipos de casos. Estos se basan en tener varios árboles de decisión, la cual aprendiendo los errores de otros árboles es que el algoritmo aprende de mejor manera. Para mejorar mucho más la capacidad de generalización de los árboles de decisión, debemos combinar varios árboles. 

Este modelo presentó una exactitud del 94,15%%, una precisión del 95,31% y una sensibilidad del 98,71% con las siguientes métricas obtenidas a partir de su respectiva matriz de confusión.
- 100 muestras fueron catalogadas como Benignas y efectivamente lo eran, mientras que 7 muestras Benignas fueron catalogadas como Malignas.
- 61 muestras fueron catalogadas como malignas y efectivamente lo eran, mientras

![image](https://github.com/CetoKaiva/ConsultoriaMACCI/assets/130872798/8e3e3994-d4dc-41c7-80e8-9227caa9b6ee)



## C.Elección y Entrenamiento del Modelo

Teniendo en cuenta los 3 modelos que se evaluaron y los resultados que se identificaron anteriormente se opta por el de regresión logística, el cual en conjunto arroja mejores resultados de los otros 2 como se puede observar en la siguiente tabla:


| Modelo             | Exactitud | Precisión | Sensibilidad |
|--------------------|-----------|-----------|--------------|
| Regresion logistica| 97.66%    | 98.48%    | 95.59%       | 
| Random Forest      | 94.15%    | 95.31%    | 98.71%       |
| SVM                | 96.49     | 95.59%    | 95.59%       |



# CONCLUSIONES

Se entrega con éxito el modelo de predicción de resultados de biopsias para determinar si es Benigno o Maligno, dicho modelo inicia con la limpieza de los datos que serán utilizados para luego analizar los datos en búsqueda de patrones que nos entregaran relaciones entre las variables mas relevantes para ser usadas en el entrenamiento de nuestros modelos elegidos, los cuales fueron : Regresión logística , SVM y Random Forest, de los cuales el de regresión logística fue el que obtuvo mejores resultados en 2 de los 3 métricas de rendimiento mas acordes con el caso, las mismas entregan un 97.66 % de exactitud al momento de clasificar un resultado, además de un 95.59% de sensibilidad, lo cual nos da mayor certeza de no evaluar de menara errada a personas que efectivamente tienen un tumor Maligno 



## Instrucciones de Uso

A continuación, se describen los pasos para utilizar el proyecto de detección de cáncer de mama.

### 1. Clonar el Repositorio

Primero, clona este repositorio en tu máquina local utilizando el siguiente comando:

```bash
git clone https://github.com/TuUsuario/ConsultoriaMACCI.git

### 2. Instalación de dependencias

pip install -r requirements.txt

### 3.Datos de Entrada

Para ejecutar las predicciones, necesitas descargar la base de datos `data_breast_cancer.csv` e incorporarla en la carpeta `data/` de este proyecto. Puedes descargarla desde el siguiente enlace:

https://github.com/CetoKaiva/ConsultoriaMACCI/blob/656bf0d4e2742dd8dad3146bab87edf346dfc65c/data_breast_cancer.csv


### 4. Ejecutar el codigo

python clasificacion_2.py
