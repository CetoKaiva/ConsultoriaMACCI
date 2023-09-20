# DIAGNÓSTICO CÁNCER DE MAMAS - Proyecto De Aprendizaje Automático Para La Detección Temprana De Cáncer De Mama.

De acuerdo a informes de la Organización Mundial de la Salud (OMS) cada año se producen 1,38 millones de nuevos casos de cáncer de mamas y 458.000 muertes (IARC Globocan, 2008). El cáncer de mama es, ampliamente, la enfermedad más frecuente en las mujeres, tanto en los países desarrollados como en los países en desarrollo, donde Chile, a nivel país, presenta una tasa de diagnósticos de 1 de cada 9 mujeres con esta enfermedad. 
Dada la importancia de la enfermedad nivel país y mundial, se escogió el tema en cuestión con el objetivo de realizar un análisis exploratorio del dataset relacionado al diagnóstico del cáncer de mamas proporcionado por la Unidad de Data Science de la Universidad de Concepción para hacer esta investigación, siendo el objetivo poder predecir el diagnóstico de un tumor si es Maligno (M) o Benigno (B) a partir de un conjunto de datos sobre el análisis de una biopsia de bulto en mama. 

El dataset dispuesto cuenta con 569 muestras, 357 de ellas benignas y 212 malignas.
Cada muestra posee una identificación (“ID”), el diagnóstico (“diagnosis”) y 30 atributos relacionados a 10 características divididas en 3 tipo variable descriptiva:
1: “Mean”, 2:” Se”, 3: “Worst”. De estas se entregan la siguiente información de cada una:


1.Radius: media de las distancias desde el centro hacia puntos del perímetro.

2.Texture: desviación estándar de las intensidades en escala de grises.

3.Perimeter: contorno de biopsia.

4.Area: superficie de la biopsia.

5.Smoothness: variación local de largo de los radios.

6.Compactness:  / área 

7.Concavity: severidad de secciones cóncavas en la delineación.

8.Concave points: número de secciones cóncavas en la delineación.

9.Symmetry: simetría de la biopsia. 

10.Fractal dimension: "Paradoja de línea de Costa" 

PARTE 1: ANÁLISIS EXPLORATORIO
A.	Limpieza Base de Datos
B.	Descripción de los Datos
C.	Análisis Gráfico (Univariables)
D.	Correlaciones entre variables

PARTE 2: MODELO PREDICTIVO
A.	División de los datos
B.	Propuesta de Modelo
  - Regresión Logística
  - SVM
  - Random Forest
C.	Elección y Entrenamiento del Modelo

CONCLUSIONES





## Cómo usar

- Paso 1: Clona este repositorio.
- Paso 2: Ejecuta el archivo `main.py`.
- Paso 3: Disfruta de tu proyecto genial!

## Contribución

Si deseas contribuir a este proyecto, sigue estas pautas de contribución.

## Licencia

Este proyecto está bajo la Licencia MIT. Consulta el archivo LICENSE para obtener más detalles.
