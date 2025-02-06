# Laboratorio 1 - Regresión

[Objetivos](#objetivos)

[Herramientas](#herramientas)

[Caso de negocio](#enunciado)

[Entregables](#entregables)

[Rúbrica de clasificación](#rubrica)


## <a name="objetivos"></a> Objetivos

- Construir modelos analíticos para estimar una variable objetivo continua a partir de un conjunto de variables observadas.

- Comprender el proceso para la construcción de modelos analíticos que responden a una tarea de regresión.

- Automatizar el proceso de construcción de modelos analíticos con el uso de pipelines de tal forma que puedan ser usados en ambientes de producción.

- Extraer información útil para el negocio a partir de los resultados de los modelos de regresión.


## <a name="herramientas"></a> Herramientas

Durante este laboratorio se trabajará con las siguientes herramientas:

- Librerías de Python para el procesamiento y analisis de datos como: 
    - Pandas
    - Scikit-Learn
    - Matplotlib, Seaborn
- Entorno de desarrollo Jupyter Lab instalado localmente mediante Anaconda o en la nube mediante Google Colab.


## <a name="enunciado"></a> Caso de Negocio: StarAlpes

Los sondeos astronómicos han emergido como herramientas fundamentales en la exploración del universo, permitiendo el estudio detallado de una amplia gama de objetos celestes. Estas exhaustivas observaciones proporcionan datos cruciales que impulsan nuestra comprensión de la evolución cósmica, desde los primeros momentos del universo hasta su estructura a gran escala. Su relevancia radica en la capacidad para revelar patrones, tendencias y fenómenos astronómicos, abriendo nuevas fronteras en la investigación cósmica. 

Uno de los sondeos más recientes es StarAlpes, cuyo objetivo es el estudio de objetos celestes en el universo, con el fin de entender fenómenos cósmicos que desafían nuestras concepciones previas. Estos extensos relevamientos nos permiten examinar una amplia variedad de sucesos astronómicos, desde la formación y evolución de galaxias hasta la actividad de cuásares distantes, pasando por la expansión continúa del universo.   

Es en este punto donde StarAlpes ha visto la oportunidad de analizar información del primer conjunto de datos obtenidos por su telescopio principal y ver si una solución basada en analítica con el uso de aprendizaje automático puede aportar en el logro de sus objetivos.  

Es relacionado con esa iniciativa que StarAlpes decidió contratarlo como científico de datos para que a partir del conjunto de datos compartido pueda aportar en el desarrollo de este estilo de proyectos que realizará la colaboración. 

Este último en particular requiere de la medición del corrimiento al rojo (redshift) de los objetos observados por su telescopio principal para determinar su distancia a la Tierra y su velocidad de alejamiento (a mayor distancia, mayor velocidad de alejamiento). Sin embargo, el cálculo del corrimiento requiere técnicas como la espectroscopia para analizar los elementos que componen los objetos observados y establecer un valor de corrimiento aproximado. Los costos en tiempo y recursos de usar instrumentos de espectroscopia para calcular las velocidades de todos los objetos en un sondeo se han vuelto prohibitivos al aumentar la cantidad de detecciones, haciendo casi imposible poder calcular el corrimiento de todas y cada una de las observaciones realizadas por el telescopio.


* [Datos de entrenamiento](train_data.csv)
* [Datos de prueba (no etiquetados)](validation_data.csv)
* [Diccionario de datos](DiccionarioDeDatos.xlsx)

## Soporte del experto

Para entender mejor los datos, un experto de StarAlpes nos dio una breve explicación del funcionamiento del telescopio. Este indicó que el instrumento captura imágenes usando una matriz de sensores a la que llegan fotones. Cada parte de esta matriz está dividida en columnas (*camcol*) y cada columna está a su vez dividida en porciones de 2048x1489 pixeles (*field*). El telescopio hace una o varias captura del cielo durante varias noches (*runs*) y para cada observación se registra la fecha de ocurrencia en dia juliano (*mjd*). Cada observación puede ser afectada por condiciones atmosféricas, perturbaciones ambientales o anomalías del telescopio, por lo cuál se marca con un flag que determina si las mediciones son confiables o no (*clean*), del mismo modo, cada porción de la matriz recibe un valor de acuerdo a la calidad local de las observaciones obtenidas. Finalmente, a cada objeto detectado se le asigna un identificador único (*objid*), se almacena sus coordenadas celestes (*ra*, *dec*), el tipo de objeto que es (*class*), y finalmente se mide la magnitud de la intensidad de luz capturada en los diferentes filtros de color: ultravioleta (*u*), verde (*g*), rojo (*r*), casi-infrarrojo (*z*) e infrarrojo (*i*). En caso de que el objeto esté desplazándose (p.ej si se trata de un objeto transitorio) se registra también su velocidad horizontal y vertical en el telescopio (*rowv* y *colv*). 


### Instrucciones

StarAlpes desea que usted los apoye en la construcción del modelo de regresión previamente descrito utilizando algunas de las etapas de la metodología "ASUM-DM":

1. **Entendimiento de los datos:** Describir las características más relevantes de los datos y todo el perfilamiento de datos, incluir el análisis de calidad de datos y hacer una preselección de las variables más importantes para la etapa de modelado.

2. **Preparación de datos:** Solucionar los problemas de calidad de datos previamente identificados que afecten el modelo a construir. Además, debe aplicar todos los proceso de preprocesamiento de datos necesarios para la construcción del modelo de regresión.

3. **Modelado:** Utilizando las variables previamente seleccionadas, construir un modelo de regresión que estime la variable objetivo con el menor error posible.

4. **Evaluación cuantitativa:** A partir de las métricas seleccionadas para evaluar y seleccionar el mejor modelo, explicar el resultado obtenido desde el punto de vista cuantitativo. Contestar a la pregunta: ¿Su equipo recomienda utilizar en producción el modelo de regresión para estimar el corrimiento al rojo? ¿Por qué? En caso de no recomendar el uso del modelo, ¿qué recomendaciones haría para continuar iterando con el objetivo de la construcción de un mejor modelo?

5. **Evaluación cualitativa:** Debe estar compuesta de dos partes:

      **- Validación de supuestos:** Realizar los ajustes necesarios para que el modelo cumpla con los supuestos necesarios para la inferencia estadística con regresiones.

      **- Interpretación de los coeficientes:** Realizar la interpretación de los coeficientes de la regresión, identificando las variables más relevantes para la estimación y cómo afectan la variable objetivo.

6. **Presentación de los resultados:** Mostrar el resultado obtenido con el modelo de regresión en una presentación corta que justifique si éste puede ayudar a cumplir el objetivo de la organización.

7. Exportar el mejor modelo (utilizando pipelines) para poder ser usado sobre datos nuevos en el ambiente de producción del cliente.

8. Generar predicciones sobre los datos de prueba que no se encuentran etiquetados utilizando el mejor modelo. Exportar las predicciones en formato CSV utlizando como base el mismo archivo de datos de prueba.

### Construcción de pipelines

Para realizar esta sección se recomienda utilizar JupyterLab para la construcción del Pipeline y la exportación del modelo. 

El objetivo de crear un [pipeline](https://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html) es automatizar todos los 
pasos realizados sobre los datos, desde que salen de su fuente hasta que son ingresados al modelo de aprendizaje automático. 
Para un problema clásico, estos pasos incluyen: la selección de características o columnas, la imputación de valores no existentes, la codificación de variables categóricas utilizando diferentes técnicas como Label Encoding o One Hot Encoding, el escalamiento de variables numéricas en caso de ser necesario y en general las diferentes tareas de transformación requeridas para la preparación de los datos. Además, como último paso, el pipeline contiene el modelo que recibe los datos después de la tranformación para realizar predicciones. Finalmente, estos pipelines pueden resultar muy útiles a la hora de calibrar y comparar modelos, pues se tiene la certeza de que los datos de entrada son los mismos para todos. Incluso, pueden ser utilizados para realizar validación cruzada utilizando GridSerchCV o RandomizedSerchCV. Así mismo, pueden ser exportados para llevar los modelos a producción por medio de la serialización de estos en archivos .pkl o .joblib. 

La librería Scikit-Learn cuenta con API para la creación de pipelines en la que pueden ser utilizados diferentes pasos para la transformación de los datos que serán aplicados secuencialmente. Note que estos pasos implementan los métodos **fit** y **transform** para ser invocados desde el pipeline. Por otro lado, los modelos que serán la parte final del proceso de automatización solo cuentan con método fit. Una vez construido el modelo es posible serializar este, haciendo uso de la función **dump** de la librería joblib, para posteriormente deserializar, cargar (mediante la función **load**) y utilizar el modelo en cualquier otra aplicación o ambiente. Tenga en cuenta que la serialización de un modelo solo incluye la estructura y configuraciones realizadas sobre el pipeline, más no las instancias de los objetos que lo componen. Pues estos son provistos por la librería, por medio de la importación, en cualquiera que sea su ambiente de ejecución. Esto significa que si usted construye transformaciones personalizadas, debe incluir por separado estas, en el ambiente donde cargará y ejecutará el modelo una vez sea exportado, ya que estas no están incluidas en la serialización. 

En este punto, debe construir un pipeline que incluya todos los pasos necesarios para transformar los datos desde el archivo fuente y que estos puedan ser utilizados para realizar predicciones.

A continuación puede encontrar algunos artículos que pueden ser de utilidad para la construcción de pipelines
<br>
<br>
[Scikit-learn Pipeline Tutorial with Parameter Tuning and Cross-Validation](https://towardsdatascience.com/scikit-learn-pipeline-tutorial-with-parameter-tuning-and-cross-validation-e5b8280c01fb)
<br>
[Data Science Quick Tip #003: Using Scikit-Learn Pipelines!](https://towardsdatascience.com/data-science-quick-tip-003-using-scikit-learn-pipelines-66f652f26954)
<br>
[Data Science Quick Tip #004: Using Custom Transformers in Scikit-Learn Pipelines!](https://towardsdatascience.com/data-science-quick-tip-004-using-custom-transformers-in-scikit-learn-pipelines-89c28c72f22a)
<br>
[Creating custom scikit-learn Transformers](https://www.andrewvillazon.com/custom-scikit-learn-transformers/)

## <a name="entregables"></a> Entregables

* Informe del laboratorio, que puede ser el mismo notebook, con el desarrollo, análisis respetivo y la evidencia de las etapas del 1 al 5.
* Presentación con los resultados para StarAlpes.
* Notebook con todo el código fuente **ejecutado**.
* Modelo integrado con pipelines exportado en formato .joblib.
* Archivo de predicciones en formato CSV utilizando como base el mismo archivo de datos de prueba.
	
Se espera que el informe incluya **JUSTIFICACIONES** de las decisiones tomadas durante la construcción e interpretación de los modelos.

## Instrucciones de Entrega
- El laboratorio se entrega en grupos de mínimo 2 y máximo 3 estudiantes.
- Recuerde hacer la entrega por la sección unificada en Bloque Neón, antes del sábado 15 de Febrero a las 20:00. Este será el único medio por el cual se recibirán entregas.
- No olvide indicar en el informe los aportes realizados por cada uno de los integrantes del grupo, según la propuesta hecha en la rúbrica.

## <a name="rubrica"></a> Rúbrica de Calificación

A continuación se encuentra la rúbrica de calificación:

| Concepto | Porcentaje |
|:---|:---:|
| 1. Descripción del entendimiento de datos  | 10% |
| 2. Descripción del proceso de selección de variables | 5% |
| 3. **Estudiante 3:** Descripción e implementación del proceso de preparación de datos (incluye la limpieza de datos) | 15% |
| 4. **Estudiante 1:** Construcción del modelo de regresión lineal y cálculo de sus métricas de calidad  | 10% |
| 5. **Estudiante 1:** Implementación del pipeline con todas las transformaciones requeridas para la generación de predicciones, exportado en formato .joblib | 15% |
| 6. **Estudiante 2:** Exploración y conclusión sobre los supuestos de la regresión a partir del modelo construido | 10% |
| 7. **Estudiante 2:** Desarrollo de las transformaciones complementarias para cumplir con los supuestos de la regresión e interpretación de los coeficientes del modelo | 15% |
| 8. **Estudiante 3:** Presentación para StarAlpes con resultados a nivel cuantitativo y cualitativo del mejor modelo construido, recomendaciones dadas a la empresa y visualizaciones extraidas del notebook | 10% |
| 9. Archivo  y resultado de predicciones sobre los datos de prueba en formato CSV. Se tomará como base el RMSE para ordenar y asignar la nota del grupo. | 5% |
| 10. Notebook ejecutado | 5% |
