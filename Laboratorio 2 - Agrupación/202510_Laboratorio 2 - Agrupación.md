# Laboratorio 2 - Agrupación

[Objetivos](#objetivos)

[Herramientas](#herramientas)

[Enunciado](#enunciado)

[Entregables](#entregables)

[Rúbrica de clasificación](#rubrica)

[Sugerencias y aclaraciones](#sugerencias)

## Objetivos

- Aplicar el proceso de aprendizaje para resolver una tarea de agrupación, desde la preparación de los datos hasta la interpretación de los resultados.
- Aplicar tres algoritmos de clústering (k-means y dos de libre elección) para resolver el objetivo de la organización.
- Determinar los hiperparámetros para la construcción de los modelos dependiendo de los algoritmos utilizados.
- Construir una tabla comparativa que muestre el rendimiento de los tres modelos de agrupación.
- Derivar conclusiones a partir de los mejores grupos identificados, que sean útiles para la organización.
- Comunicar los hallazgos encontrados a la organización, explicando por qué tienen valor para el negocio.

## Herramientas

Durante este laboratorio trabajaremos con las siguientes herramientas:

- Python
  - Distribución sugerida: [Anaconda](https://www.continuum.io/downloads)
  - Ambiente de desarrollo
    - JupyterLab
    - Google Colab
  - Librerías
    - Pandas
    - Scikit-learn
    - Matplot
    - Seaborn

## Enunciado

### Descripción del problema

La agrupación es una técnica de aprendizaje no supervisado que permite identificar patrones y tendencias en los datos con base en la identificación de grupos o segmentos de objetos con características comunes. Por ejemplo, para el caso una empresa que ofrece servicios de tarjetas de crédito, la segmentación de clientes facilitaría la personalización de productos y servicios de acuerdo con las necesidades y comportamientos específicos de cada grupo identificado. Además, se podrían dirigir campañas de marketing a segmentos particulares, optimizando la comunicación y mejorando la experiencia de los clientes a través de un servicio de atención más ajustado a sus preferencias y hábitos.
En este marco, FinanzasAlpes, una empresa emisora de tarjetas de crédito, busca segmentar a sus clientes según su comportamiento de compra en centros comerciales, con el objetivo de identificar los distintos perfiles de tarjetahabientes y desarrollar estrategias de marketing personalizadas para cada segmento. Para llevar a cabo este estudio, la empresa nos ha contratado como científicos de datos y nos ha proporcionado un conjunto de datos sobre sus clientes, que incluye información detallada sobre saldos, límites de crédito, hábitos de compra y otros aspectos relevantes.

* [Datos de entrenamiento](https://gitlab.virtual.uniandes.edu.co/ISIS3301/laboratorios/blob/master/202510/Laboratorio%202%20-%20Agrupaci%C3%B3n/Customer_Data.csv)
* [Diccionario de datos](https://gitlab.virtual.uniandes.edu.co/ISIS3301/laboratorios/blob/master/202510/Laboratorio%202%20-%20Agrupaci%C3%B3n/Diccionario_Customer_data.xlsx)

### Instrucciones

FinanzasAlpes desea que usted los apoye en la construcción del modelo de agrupación previamente descrito con base en las etapas de la metodología "CRISP-ML":

1. **Preparación de datos:** Realizar la preparación de los datos teniendo en cnuenta las características de los algoritmos de agrupación a emplear.
2. **Modelamiento:** Aplicar el algoritmo K-Means y otros dos algorimos para construir tres modelos de agrupación. Tengan en cuenta que, en ambientes profesionales, la elección y justificación del algoritmo y sus hiperparámetros hace parte de su tarea de consultoría.
3. **Validación cuantitativa (Evaluación):** La calidad desde el punto de vista cuantitativo puede validarse utilizando diferentes métricas intrínsecas, como el coeficiente de silueta.
4. **Validación cualitativa (Evaluación):** Una vez realizada la validación cuantitativa, se debe hacer una descripción de los grupos obtenidos, apoyada en formas de visualizar los resultados, y relacionarlo con el objetivo que tiene la organización para determinar si es posible utilizar el resultado obtenido, o hay que seguir trabajando en alguna dirección específica para la comprensión por parte de la organización.

## Entregables

- Informe, que puede ser el mismo cuaderno, el cual debe incluir:
  - Descripción detallada de cada etapa según las instrucciones dadas previamente
  - Indicar el nombre del estudiante que desarrolló cada algoritmo y una descripción general de cómo funciona.
- Presentación de diapositivas con los resultados.
- Cuaderno ejecutado.

Algunas preguntas que pueden guiar su desarrollo son:

1. ¿Qué criterios son importantes para la selección del modelo?
2. ¿Cómo medir la calidad del modelo construido? ¿Cómo saber que el modelo construido tiene una buena calidad?
3. ¿Qué retos tienen estos modelos no supervisados, si se quisieran aplicar a nivel profesional?
4. ¿Cómo varía la calidad de la solución obtenida si se aplican diferentes algoritmos?

**Nota:**
Recuerde que la presentación debe estar orientada a la organización, por lo que se recomienda evitar el uso de términos muy técnicos y utilizar un lenguaje que sea familiar en el contexto de aplicación. Se les sugiere centrarse en la interpretación de los resultados.

## Instrucciones de Entrega

- El laboratorio se entrega en grupos de mínimo 2 y máximo 3 estudiantes. Estos estudiantes pueden ser de diferentes secciones.
- Recuerde hacer la entrega por la sección unificada en Bloque Neón, antes del sábado 15 de marzo a las 20:00.
  Ese será el único medio por el cual se reciben entregas.

## Rúbrica de Calificación

A continuación se encuentra la rúbrica de calificación.

**Nota:** Los siguientes porcentajes hacen referencia a la nota grupal, que corresponde a un 80% de la nota inidiviudal.
El 20% restante se calcula según el puntaje obtenido en la implementación del algoritmo del cual el estudiante estuvo a cargo dentro del grupo.

| Concepto                                                                                                                                                                                                                     | Porcentaje |
| :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------: |
| Descripción del proceso de limpieza y preparación de datos realizado, teniendo en cuenta los algoritmos utilizados. Justitificar utilizando el entendimiento de los datos                                                  |    15%    |
| **Estudiante 1:** Implementación de K-means, descripción de las decisiones más importantes asociadas a la implementación del algoritmo y los hiperparámetros configurados                                         |    15%    |
| **Estudiante 2:** Implementación de un segundo algoritmo de libre elección, descripción corta del algoritmo y de las decisiones más importantes asociadas a la implementación y los hiperparámetros configurados |    15%    |
| **Estudiante 3:**  Implementación de un tercer algoritmo de libre elección, descripción corta del algoritmo y de las decisiones más importantes asociadas a la implementación y los hiperparametros configurados  |    15%    |
| Análisis de los resultados obtenidos y justificación del modelo recomendado para el caso propuesto                                                                                                                         |    25%    |
| Presentación de diapositivas para la organización con resultados, con las recomendaciones                                                                                                                                  |    10%    |
| Cuaderno asociado, ejecutado                                                                                                                                                                                                 |     5%     |

## Sugerencias y aclaraciones

- Nota 1: la interpretación de los grupos se debe hacer en términos de las variables que consideren importantes (incluya las usadas para la construcción de los clusters
  pero también otras variables, que no hayan incluido)
- Nota 2: Analizar si los valores de cada columna corresponden a valores adecuados para el negocio, en caso de que no lo sean, deben tratar dichos valores y justificar sus decisiones.

Los siguientes enlaces pueden serle de utilidad para la implementación en Python.

* [Ejemplo de K-Means usando Sklearn](https://jakevdp.github.io/PythonDataScienceHandbook/05.11-k-means.html)
* [Artículo de Towards Data Science: Mastering K-Means Clustering](https://towardsdatascience.com/mastering-k-means-clustering-065bc42637e4/)
* [Artículo de Towards Data Science: Best Practices for Visualizing Your Cluster Results](https://towardsdatascience.com/best-practices-for-visualizing-your-cluster-results-20a3baac7426)

- Cada integrante del grupo debe estar encargado de la implementación de un algoritmo distinto. Sin embargo, todos los integrantes del grupo
  deben tener la capacidad de explicar lo realizado por los demás compañeros
- El análisis de resultados y su justificación debe ser realizado en grupo.
