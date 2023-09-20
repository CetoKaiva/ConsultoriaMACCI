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


![image](https://github.com/CetoKaiva/ConsultoriaMACCI/assets/130872798/d7831c4a-2623-4503-a2ea-fe014bdde831)




