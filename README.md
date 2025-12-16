
# Análisis Exploratorio de Datos del Proceso de Suscripción a Depósitos Bancarios

## 1. 📝 Introducción

Este proyecto tiene como finalidad analizar en profundidad el comportamiento de los clientes contactados durante diversas campañas de marketing telefónico realizadas por una entidad bancaria, con el objetivo de promover la contratación de un depósito a plazo. 

A partir de una combinación de datos demográficos, características socioeconómicas, información macroeconómica y registros históricos de interacción, se desarrolla un proceso completo de análisis exploratorio destinado a identificar patrones, perfiles y factores que influyen en la probabilidad de conversión. 

El trabajo sigue un flujo estructurado que abarca todas las etapas fundamentales de un proceso analítico. En primer lugar, se realiza un análisis preliminar para comprender la estructura y calidad de los datos. 

Posteriormente, se lleva a cabo una limpieza y transformación exhaustiva del dataset, garantizando su integridad y adecuación para el análisis. Adicionalmente, se generan nuevas variables, incluyendo métricas temporales y atributos derivados del comportamiento de los clientes, para mejorar la capacidad explicativa del conjunto de datos.

A continuación, se desarrolla un análisis exploratorio detallado, tanto univariante como bivariante, orientado a identificar patrones relevantes, relaciones significativas y factores que influyen en la probabilidad de que un cliente contrate el producto. 

Este análisis permite caracterizar los perfiles de mayor y menor propensión a suscribir el depósito, así como detectar tendencias temporales y comportamientos diferenciados según segmentos.

El resultado final del proyecto busca proporcionar una comprensión sólida del proceso de captación de clientes y de las variables que más contribuyen a la conversión, permitiendo optimizar recursos, mejorar la segmentación y aumentar la eficacia comercial, para la planificación estratégica de futuras campañas.

## 2. 📌 Objetivos del Análisis

### Objetivo General

El objetivo principal del proyecto es realizar un análisis exploratorio para comprender en profundidad la estructura, distribución y relaciones existentes entre las variables que describen a los clientes y el contexto de la campaña, con el fin de identificar patrones relevantes que puedan influir en la suscripción del depósito a plazo.

Mediante la integración de información de ambas bases de datos y la evaluación de sus características, se busca sentar las bases para el desarrollo de modelos predictivos y para la optimización de estrategias comerciales dirigidas a mejorar la eficacia de futuras campañas.

### Objetivos Específicos

- ***Analisis Preliminar*** : Realizar una revisión inicial de las bases de datos para examinar la estructura y composición de los datos disponibles, identificando tipos de variables, niveles de calidad de la información, presencia de anomalías y posibles inconsistencias que puedan influir en el análisis posterior, así como cualquier aspecto que requiera intervención antes del análisis.

- ***Limpieza de Datos*** : Depurar el conjunto de datos mediante el tratamiento de valores faltantes, corrección de inconsistencias, eliminación de duplicados,  supresión de variables irrelevantes y posibles errores de registro. Asimismo, se incorporan transformaciones necesarias, como recodificaciones, ajustes de formatos y creación de nuevas variables derivadas para optimizar la interpretabilidad y utilidad del dataset.

    Además, se procede a unificar las fuentes de información **bank-additional.csv** y **customer-details.xlsx**, asegurando la consistencia y calidad del dataset, y dando lugar a la construcción de **df_final**, el conjunto de datos integrado utilizado para el análisis.

- ***Análisis Exploratorio de Datos (EDA)*** : Examinar de manera detallada las relaciones entre variables mediante técnicas univariantes y bivariantes, identificando patrones, tendencias y factores potencialmente influyentes en la suscripción del producto.

## 3. 🧱 Estructura del Proyecto

```bash
|------ data # Conjunto de datos utilizados en el proyecto.
  |---- 0.1 raw # Datos originales sin procesar.
    |--- bank-additional.csv # Dataset inicial de campañas de marketing.
    |--- customer-details.xlsx # Archivo original con información de clientes.
  |---- 0.2 processed # Datos transformados y listos para el análisis.
    |-- bank_additional_limpio.csv # Versión depurada del dataset de  campañas.
    |-- customer-details_limpio.csv # Datos de clientes limpios y estandarizados.
    |-- df_final.parquet # Dataset unificado y preparado para el análisis final.
    |-- df_final_eda.parquet # Dataset final con las variables creadas en el EDA.
|------ notebook # Notebooks con el desarrollo del análisis.
    |--- 0.1-Analisis_preliminar.ipynb # Exploración inicial y revisión del estado de los datos.
    |--- 0.2_Limpieza.ipynb # Procesos de depuración y transformación del dataset.
    |--- 0.3_Proyecto_EDA.ipynb # Análisis exploratorio completo y visualizaciones.
|------ README.md # Documento principal con la descripción general del proyecto.
```
## 4. 🗃️ Descripción del Conjunto de Datos 

Este conjunto de datos contiene información sobre clientes bancarios y su comportamiento durante las campañas de marketing telefónico.

Los archivos utilizados para la creación de este conjunto de datos provienen de:

### `bank-additional.csv` (Actividad de Marketing)

●	**age**: La edad del cliente.

●	**job**: La ocupación o profesión del cliente.

●	**marital**: El estado civil del cliente.

●	**education**: El nivel educativo del cliente.

●	**default**: Indica si el cliente tiene algún historial de incumplimiento de pagos (1: Sí, 0: No).

●	**housing**: Indica si el cliente tiene un préstamo hipotecario (1: Sí, 0: No).

●	**loan**: Indica si el cliente tiene algún otro tipo de préstamo (1: Sí, 0: No).

●	**contact**: El método de contacto utilizado para comunicarse con el cliente.

●	**duration**: La duración en segundos de la última interacción con el cliente.

●	**campaign**: El número de contactos realizados durante esta campaña para este cliente.

●	**pdays**: Número de días que han pasado desde la última vez que se contactó con el cliente durante esta campaña.

●	**previous**: Número de veces que se ha contactado con el cliente antes de esta campaña.

●	**poutcome**: Resultado de la campaña de marketing anterior.

●	**emp.var.rate**: La tasa de variación del empleo.

●	**cons.price.idx**: El índice de precios al consumidor.

●	**cons.conf.idx**: El índice de confianza del consumidor.

●	**euribor3m**: La tasa de interés de referencia a tres meses.

●	**nr.employed**: El número del empleado.

●	**y**: Indica si el cliente ha suscrito un producto o servicio (Sí/No).

●	**date**: La fecha en la que se realizó la interacción con el cliente.

●	**id_**: Un identificador único para cada registro en el dataset.

### `customer-details.xlsx` (Base de Clientes)

●	**Income**: Representa el ingreso anual del cliente en términos monetarios.

●	**Kidhome**: Indica el número de niños en el hogar del cliente.

●	**Teenhome**: Indica el número de adolescentes en el hogar del cliente.

●	**Dt_Customer**: Representa la fecha en que el cliente se convirtió en cliente de la empresa.

●	**NumWebVisitsMonth**: Indica la cantidad de visitas mensuales del cliente al sitio web de la empresa.

●	**ID**: Identificador único del cliente.

### `df_final` (Dataset Integrado)

Además de las variables ya descritas en los apartados anteriores, se incluyen las siguientes variables adicionales:

- **year_contact**: Año de la interacción con el cliente, extraído a partir de **date**.

- **month_contact**: Mes de la interacción con el cliente, en formato numérico (1–12), derivado de **date**.

- **year_customer**: Año de alta del cliente en la entidad, obtenido a partir de **Dt_Customer**.

- **month_customer**: Mes de alta del cliente, en formato numérico (1–12), derivado de **Dt_Customer**.

- **days_until_signup**: El número de días transcurridos entre la fecha del contacto actual **date** y la fecha en la que el cliente se dio de alta en la empresa **Dt_Customer**. Esta variable proporciona información sobre el tiempo entre la adquisición del cliente y el primer contacto.

- **days_until_signup_num**: Versión numérica de **days_until_signup**, expresada en días. Se obtiene mediante la conversión de la variable **days_until_signup** a días. 

  (Esta conversión se lleva a cabo porque `pd.cut()` no admite directamente valores de tipo `timedelta64`, por esta razón, es necesario transformar la diferencia temporal a un formato numérico en días para permitir una correcta segmentación y análisis.)

- **time_until_signup**: Esta variable agrupa a los clientes en intervalos de tiempo según el número de días transcurridos desde su alta en la empresa, usando los siguientes grupos: `< 6 meses`, `6–12 meses`, `1–2 años`, `> 2 años`

## 5. ⚙️ Instalación y requisitos

El proyecto se ha desarrollado en un entorno **Python**, empleando un conjunto de librerías orientadas a la gestión eficiente de datos y a la generación de visualizaciones analíticas:

- **Pandas y NumPy**: Herramientas para la manipulación, limpieza y transformación numérica del dataset.

- **Matplotlib y Seaborn**: Librerías utilizadas para la creación de gráficos descriptivos que permiten explorar patrones, distribuciones y relaciones entre variables.

- **Locale**: Configuración del formato regional para el tratamiento adecuado de fechas y valores específicos del entorno español.

- **Parquet**: Formato de almacenamiento que facilita operaciones de lectura y escritura de forma más rápida y eficiente, optimizando el manejo del dataset.

## 6. 🕒 Recap Sesiones 

### Sesión 1

- Creación del repositorio en Github.

- Creación del sistema de carpetas del repositorio.

- Generación del archivo README.

- Se añade el conjunto de datos original `'bank-additional.csv'`.

- Se añade el conjunto de datos original `'customer-details.xlsx'`.

### Sesión 2

- Creación del notebook `'0.1-Analisis_preliminar.ipynb'`.

- Se lleva a cabo un análisis preliminar de las bases de datos `'bank-additional.csv'` y `'customer-details.xlsx'`, con el fin de identificar el tipo de datos que presentan sus variables, evaluar su coherencia y detectar aspectos que requieren de intervención. 

  Además se realiza la verificación de valores atípicos, nulos y la identificación de posibles registros duplicados, proporcionando así una visión inicial del estado y la calidad de la información.

### Sesión 3

- Creación del notebook `'0.2_Limpieza.ipynb'`.

- Se lleva a cabo un proceso de limpieza y transformación de los archivos `'bank-additional.csv'` y `'customer-details.xlsx'`, corrigiendo aquellos tipos de datos que no se corresponden con el contenido real de las variables, además se tratan los valores nulos y los registros duplicados. De este modo, los conjuntos de datos quedan correctamente depurados y normalizados, garantizando su coherencia para las fases posteriores del análisis.

- Los nuevos conjuntos de datos se guardan como `'bank-additional_limpio.csv'` y `'customer-details_limpio.csv'`. La base de datos de clientes se guarda en formato **CSV** con el objetivo de facilitar su posterior integración con el resto de las fuentes de información, garantizando una unión más sencilla y consistente entre ambos datasets.

### Sesión 4

- Se procede a la integración de las dos fuentes de datos ya listas, `'bank-additional_limpio.csv'` y `'customer-details_limpio.csv'`. Como resultado de esta unión se genera un nuevo conjunto de datos unificado, denominado `'df_final'`, que consolida la información relevante de ambas bases de datos y constituye la base principal para el desarrollo del análisis exploratorio de datos.

- Se realiza una verificación exhaustiva del conjunto de datos `'df_final'` con el objetivo de confirmar que todas las variables presentan valores coherentes con su naturaleza, así como de asegurar la ausencia de registros duplicados y valores nulos.

- Se procede a guardar el nuevo dataset resultante en formato **Parquet**, generando `'df_final.parquet'`, ya que este formato ofrece una gestión más eficiente de la información, optimizando el rendimiento en las operaciones de lectura y escritura y facilitando su uso en las etapas posteriores del análisis.

### Sesión 5

- Creación del notebook `'0.3_Proyecto_EDA.ipynb'`.

- Realización del análisis exploratorio de datos (EDA) sobre el conjunto de datos `'df_final.parquet'`, con el objetivo de comprender en profundidad la estructura del dataset y el comportamiento de sus variables.

  Este análisis incluye el estudio descriptivo de variables numéricas y categóricas, la identificación de distribuciones, patrones y posibles relaciones entre atributos, así como la detección de tendencias relevantes que puedan influir en la variable objetivo. De este modo, se obtienen conclusiones sólidas que sirven de base para el desarrollo del análisis.

- Se guarda el conjunto de datos `'df_final_eda'` incorporando todas las variables generadas durante el EDA para asegurar la coherencia del análisis y facilitar su uso en etapas posteriores.

### Sesión 6

- Elaboración y redacción de los resultados obtenidos a lo largo del análisis, junto con la formulación de conclusiones. 

- Se elabora un informe detallado en el que se documenta de manera estructurada el proceso realizado, las observaciones más relevantes, los principales hallazgos obtenidos y las conclusiones e implicaciones derivadas del análisis.

## 7. 🧠 Resultados y Conclusiones

El análisis exploratorio de datos ha permitido obtener una visión detallada del comportamiento de los clientes y de los factores asociados a la contratación del depósito. 

Se confirma un fuerte desbalance en la variable objetivo `'y'`, ya que aproximadamente el **89 %** de los clientes **no** contrata el producto, frente a solo un **11 %** que **sí** lo hace, lo que condiciona tanto la interpretación de los resultados como futuras fases de modelización.

Entre las variables numéricas, la duración de la llamada destaca como el factor con mayor capacidad discriminante entre clientes que contratan y aquellos que no. La mediana de la duración pasa de aproximadamente **163 segundos** en el grupo que **no** contrata a **453 segundos** en el grupo que **sí** lo hace, lo que sugiere que interacciones más prolongadas se asocian con una mayor probabilidad de conversión. <br>
Por su parte, las variables macroeconómicas presentan diferencias consistentes entre ambos grupos, reflejando que el entorno economico en el momento del contacto influye en la probabilidad de éxito. Los clientes que contratan tienden a estar asociados a valores más bajos de indicadores como `'euribor3m'` y `'emp.var.rate'`, lo que coincide con periodos económicos más favorables y refuerza la idea de que el entorno economico influye de forma relevante en el éxito de la campaña.

El análisis de las variables categóricas revela diferencias significativas en la tasa de contratación según características como la ocupación, donde se muestra variaciones claras, los colectivos como **estudiantes** y **jubilados** alcanzando tasas de conversión superiores al **25 %**, frente a otros grupos como los **obreros** o **servicios**, que apenas superan el **7–8 %**. <br>
Asimismo, el resultado de campañas previas constituye uno de los factores más determinantes, los clientes con un **resultado previo exitoso** presentan una tasa de contratación cercana al **65 %**, mientras que aquellos **sin contactos anteriores** o con **resultados negativos** se sitúan por debajo del **15 %**. <br>
En cuanto al canal de contacto, el uso de **teléfono móvil** (cellular) muestra una tasa de conversión superior al **14 %**, frente al contacto por **teléfono fijo** (telephone), que apenas alcanza el **5 %**. <br>
Por el contrario, otras variables categóricas como el **estado civil** o el **nivel educativo** presentan distribuciones más homogéneas y un impacto menos acusado sobre la probabilidad de contratación.

Desde el punto de vista temporal, se observa que los clientes con menor antigüedad presentan una mayor propensión a contratar el producto, en comparación con aquellos con mayor antigüedad, mientras que los clientes con una antigüedad inferior a **6 meses** muestran tasas de contratación superiores al **15 %**, se advierte que este porcentaje desciende progresivamente en los segmentos de mayor antigüedad, situándose por debajo del **10 %** en clientes con más de **2 años**.

Por otro lado, el análisis temporal de contacto no revela patrones estacionales claramente definidos, ya que las variaciones observadas a lo largo del tiempo son moderadas y no siguen una tendencia consistente. 

En conclusión, el análisis exploratorio confirma que la probabilidad de contratación del depósito no responde a un único factor, sino a la interacción de múltiples factores relevantes que actúan de forma conjunta. La fuerte diferencia de la variable objetivo `'y'` condiciona el enfoque analítico y requiere técnicas específicas en etapas posteriores. La duración de la llamada aparece como el principal indicador asociado a la conversión, mientras que el entorno macroeconómico en el momento del contacto también influye de forma significativa en la decisión del cliente. <br> 
Asimismo, variables relacionadas con el perfil del cliente y el historial de contacto, como la ocupación, el resultado de campañas previas y el canal utilizado, aportan información relevante para identificar segmentos con mayor probabilidad de respuesta.<br>
Desde el punto de vista temporal, los clientes con una incorporación más reciente muestran una mayor predisposición a contratar, lo que sugiere oportunidades claras para focalizar las campañas.

Los resultados obtenidos permiten identificar perfiles con mayor probabilidad de conversión y proporcionan una base sólida para el desarrollo de modelos predictivos y para la toma de decisiones estratégicas orientadas a mejorar la eficacia de las campañas.

## 8. 🤝 Contribuciones

- Cualquier contribucion es bien venida, si quiere colaborar en el proyecto, abre un pull request.

## 9. ✍️ Autores

- Carlos Hernando

- https://github.com/C4rl0s1515
