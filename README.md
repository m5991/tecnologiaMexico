# Uso de la tecnologia en México

Por: Manuel Gastelum, Ricardo Gutiérrez y Gabriel Varela

Este proyecto que se muestra a continuación contiene una muestra de datos sobre el uso de la tecnología en México; el uso de las diferentes tic's como el uso del internet y sus diferentes variables provenientes de la encuesta del INEGI. Se limpiaron los datos para buscar una relación de los servicios y comodidades en función del nivel académico.

# Introducción 

El alcance de la tecnología dentro de la globalización en la última década se ha puesto al alcance de toda la población. La "Encuesta Nacional sobre Disponibilidad y Uso de Tecnologías de la Información en los Hogares (ENDUTIH) 2021" es el nombre de la encuesta realizada por el INEGI con una muestra de aproximadamente de 60,000 viviendas encuestadas, en total son 200,000 personas en las 32 entidades del país a las que se les realiza este cuestionario aproximadamente. Fuente: [INEGI](https://www.inegi.org.mx/programas/dutih/2021/) muestra algunas características de internet, telefonía y computación para el entretenimiento, educación, redes sociales y comunicación, capacitación, trabajo/empresa y ventas por internet (e commerce).

El software utilizado en este trabajo es python 3 con apoyo de la herramienta de jupyter notebook asimismo, comienza con un análisis exploratorio (EDA) que nos arroja algunas características importantes, relevantes para el uso de algún algoritmo. Se utilizan diferentes herramientas de python como Altair, geojson y skitlearn para descifrar y entender la información que ofrecen los datos. Las herramientas en manos de científicos de datos intentan clasificar los servicios y comodidades en función de su grado académico. 

Es importante mencionar al lector que existen algunas impresiones en el uso de los datos durante la limpieza para facilitar el análisis, debido a que el diccionario puesto por el INEGI puede resultar ambiguo, esto puede afectar en el resultado final como se verá en la siguientes secciones de este trabajo.



# Resultados

Los resultados de esta exploración y entrenamiento se pueden ver leer con mayor detalle en el siguiente [documento](doc/Resultados.md).

Estos fueron ejecutados en los siguientes notebooks:

1. [Limpieza de datos](src/01%20%20Limpieza%20de%20datos.ipynb).
2. [Análisis de resultados](src/02%20Analisis%20Resultados.ipynb).
3. [Árbol de decisión para el nivel educativo del jefe de vivienda](src/03%20Arbol%20de%20Decision%20-%20efe%20de%20Familia.ipynb).
4. [Árbol de decisión para el nivel educativo de la persona con máximo nivel de extudios en la vivienda](src/04%20Arbol%20de%20Decision%20-%20Nivel%20Maximo%20Estudios.ipynb).

## Análisis Exploratorio de Datos (EDA)

En este apartado se muestra la exploración de los datos después de la limpieza y organización en función del problema. Comenzamos por saber el muestreo que realizó INEGI, en promedio por estado son 1800 registros tomando como base el jefe de familia (proveedor) como se puede observar en la siguiente imagen:

| ![](results/mapa_total.png) |
|:--:|
| <b>Mapa de cantidad de personas en el registro por entidad federativa</b>|

De lo anterior nos damos cuenta de la proporción de hombres y mujeres como jefa de familia, el nivel educativo en función de la edad, el uso de la tecnología, etc., se generan preguntas que se abordarán en las discusiones más adelante como ¿Mantiene a la familia o es madre soltera?, ¿las generaciones de 60 años o más se les dificulta el uso de la tecnología?, invariablemente todos usan el internet de manera primaria, secundaria o terciaria ¿El uso del internet se ha vuelto una necesidad en todos los estratos sociales?, entre otras más situaciones.

Al mismo tiempo se explora al jefe de familia por sexo, edad, nivel educativo, uso de la computadora y el uso del internet en un tiempo no mayor a 3 meses. Posterior a esto, se aplica un filtro para el estado de Jalisco para entender si el comportamiento es similar a lo que se observa con la muestra completa de los datos. El estado de Jalisco tiene un comportamiento promedio respecto a la muestra, la edad en función del nivel académico nos arroja que a mayor edad el nivel educativo se queda en primaria y secundaria, si la edad es de 20 años hasta los 50 años existe una mayor población con preparatoria y licenciatura con una minoría en educación especializada. En el rango 10 a 20 años no existe como tal un nivel educativo debido que son los años de conclusión de los estudios de primaria, secundaria, bachillerato y licenciatura como se muestra en la siguiente imagen:

| ![](results/edad_nivel_jal.png) |
|:--:|
| <b>Número de registros de jefes de vivienda por nivel educativo y edad en el estado de Jalisco</b>|




## Modelo de clasificación por árboles de decisión

Se realiza el entrenamiento en dos conjuntos distintos, uno corresponde al nivel educativo del jefe de la vivienda y el otro al máximo nivel educativo logrado por alguno de los habitantes de la vivienda.

En esta primer entrenamiento puede observarse que el Uso de la computadora en los últimos 3 meses (P_3_9_1) es el nodo principal de la clasificación, seguido del uso del internet en los últimos 3 meses. 

| ![](results/arbol_decision_jefe_familia.png) |
|:--:|
| <b>Arbol de decisión para clasificar el nivel educativo (reestructurado) para el jefe de vivienda en México</b>|

En esta clasificación se obtienen resultados parecidos (1ro y 2do nodo).

| ![](results/arbol_decision_nivel_max_estudios.png) |
|:--:|
| <b>Arbol de decisión para clasificar el nivel educativo (reestructurado) para la persona con máximo nivel de estudios en la vivienda</b>|

Con estos árboles podemos hablar que el uso de la computadora y el internet si ayuda a predecir el nivel educativo de las personas en la vivienda (jefe y máximo nivel de estudios). 

# Divulgación

Este proyecto fue compartido públicamente en LinkedIn y la publicación puede ser encontrada en el siguiente [enlace](https://www.linkedin.com/feed/update/urn:li:activity:7061112250903756800?updateEntityUrn=urn%3Ali%3Afs_feedUpdate%3A%28V2%2Curn%3Ali%3Aactivity%3A7061112250903756800%29).


# Referencias

- Amat Rodrigo, J. (s. f.). Arboles de decision python. Cienciadedatos.net. https://www.cienciadedatos.net/documentos/py07_arboles_decision_python.html

- scikit-learn: machine learning in Python — scikit-learn 0.16.1 documentation. (s. f.-b). https://scikit-learn.org/

- pandas - Python Data Analysis Library. (s. f.). https://pandas.pydata.org/

- INEGI. Encuesta Nacional sobre Disponibilidad y Uso de Tecnologías de la Información en los Hogares (ENDUTIH) 2021. https://www.inegi.org.mx/programas/dutih/2021/
