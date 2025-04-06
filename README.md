# PROYECTO FINAL ETL - 2025

# TÍTULO: FORTALECIMIENTO DE LA DETECCIÓN TEMPRANA DEL CÁNCER DE MAMA EN COLOMBIA: UN ENFOQUE INTEGRAL PARA REDUCIR LA MORTALIDAD
## INTEGRANTES DEL GRUPO:
+ **José Vicente ALZATE GUERRERO** (Cód. 22502201)  
+ **Jonathan Giraldo DÍAZ ORTEGA** (Cód. 22501577)  
+ **Fabio Alejandro SASTOQUE** (Cód. 22502053)  
+ **Roberto Carlos TIERNO** (Cód. 22500842)

## FORMULACIÓN DEL PROBLEMA
El cáncer de mama representa una de las principales amenazas para la salud de las mujeres a nivel mundial. En Colombia, esta enfermedad constituye la primera causa de mortalidad por cáncer en la población femenina, con aproximadamente 3,000 muertes anuales [2], [15]. A pesar de los avances en tratamientos y tecnologías de detección, Colombia enfrenta desafíos significativos en la implementación efectiva de programas de detección temprana [1], [5], lo que resulta en diagnósticos tardíos y, consecuentemente, en tasas de supervivencia más bajas en comparación con países desarrollados.
Este   proyecto   busca   identificar   las   problemáticas   específicas   que   limitan   la efectividad  de  los  programas  de  detección  temprana  del  cáncer  de  mama  en Colombia y proponer soluciones integrales que permitan mejorar y ampliar estos servicios. Mediante un análisis exhaustivo de la situación actual, se pretende desarrollar estrategias que consideren las particularidades socioculturales, económicas y geográficas del país, con el objetivo final de reducir la mortalidad por esta enfermedad y mejorar la calidad de vida de las mujeres colombianas.  

## JUSTIFICACIÓN
El cáncer de mama es la primera causa de mortalidad por cáncer en mujeres colombianas [2], [15]. Mejorar su detección temprana tendría un impacto significativo en la reducción de la mortalidad y la morbilidad asociadas [8]. Por otra parte, la detección temprana reduciría los costos de tratamiento. Según estudios económicos, el diagnóstico en etapas avanzadas puede costar hasta 5 veces más que el tratamiento en etapas iniciales [9], [12]. La detección temprana puede incrementar las tasas de supervivencia a 5 años del 56% actual a más del 85% [5], [8], como ocurre en países con programas efectivos.
Por otra parte, no puede omitirse que Colombia  ha suscrito compromisos  internacionales para reducir la mortalidad por enfermedades no transmisibles, incluido el cáncer de mama. Fortalecer los programas de detección temprana es fundamental para cumplir estos compromisos. Si hablamos de asuntos de equidad, el mejorar el acceso a servicios de detección temprana contribuye a reducir las desigualdades en salud que afectan desproporcionadamente a mujeres de estratos socioeconómicos bajos y de zonas rurales.

## REQUERIMIENTOS

## FORMA DE EJECUCIÓN
La Aplicación puede ejecutarse en línea con el acceso (link) correspondiente.
La aplicación puede consultarse en: https://uao-my.sharepoint.com/:u:/g/personal/fabio_ale_sastoque_uao_edu_co/EYi7O03Jdk1IknX6RQJnPNoBIgJnELhnP6odvMTA9_IkqA?e=sH33hd
## DIAGRAMA EN BLOQUES

## DIAGRAMA DE FLUJO
  <img decoding="async" src="https://github.com/Roberto-Tierno/Breast_Cancer/blob/main/img/Flujo%20ETL-FLUJO.jpg" alt="Diagrama de Flujo" width="100%">

## ESTRUCTURA DEL REPOSITORIO
  <img decoding="async" src="https://github.com/Roberto-Tierno/Breast_Cancer/blob/main/img/Flujo%20ETL-TREE.jpg" alt="Diagrama de Flujo" width="60%">

## FUENTES
Se cuenta con un dataset principal que resalta resultados propios de Colombia y otro dataset complementario además de fuentes de información consolidadas, que permitirán obtener el contexto internacional sobre el que se deberá comparar el dataset principal. 
| Dataset | Descripción | Disponible en |
| --- | --- | --- |
| Repositorio | Enlace al repositorio GitHub | [Enlace 1](https://github.com/jonathandzrtg/Breast_Cancer/tree/main) |
| Datalake | Datalake donde se almacenan los datos utilizados | [Enlace 2](https://portal.azure.com/#@uao.edu.co/resource/subscriptions/59597407-4315-4383-9580-291cd449d59a/resourceGroups/gr-etl-uao/providers/Microsoft.Storage/storageAccounts/azdletluao/overview) |
| Azure SQL Database Sink| Base de Datos de Azure| [Enlace 3](https://portal.azure.com/#@uao.edu.co/resource/subscriptions/59597407-4315-4383-9580-291cd449d59a/resourceGroups/gr-etl-uao/providers/Microsoft.Sql/servers/server-uao-etl/databases/uao-etl/queryEditor) |

En caso de requerir contraseña, puede acceder con los datos: 

| Usuario | Contraseña |
| --- | --- |
| *useruao* | *Passuao123* |

## EXTRACCIÓN DE DATOS
+ Para la extracción, se utiliza una metodología de extracción simple de pandas. Se carga  el  dataset  desde  un  archivo  CSV  llamado  'Breast_Cancer.csv'  utilizando pandas.
+ Se implementó  un datalake  en Azure  como  fuente  para no  cargar  localmente  el archivo y para que permaneciera accesible en la nube.


## ANÁLISIS EXPLORATORIO DE DATOS (EDA)  
Antes de la transformación, se realiza una exploración detallada, donde se procede a la visualización de los primeros registros para entender la estructura, se analizan de dimensiones (4024 filas y 16 columnas), se evalúa la información sobre tipos de datos (5 columnas numéricas y 11 categóricas) y se obtiene un análisis estadístico de variables numéricas (media, desviación estándar, mínimos, máximos) con la identificación de valores únicos en variables categóricas.

### Estadísticas de edad: 
El análisis de la distribución de la edad en la población estudiada revela una media de 59.95 años y una mediana de 60 años, lo que sugiere una distribución aproximadamente simétrica. La desviación estándar de 13.83 años indica una variabilidad moderada en los datos, mientras que el rango de edades, comprendido entre 23 y 92 años, muestra una amplitud de 69 años. La similitud entre la media y la mediana sugiere que la distribución no presenta una asimetría significativa, aunque podrían existir ligeras desviaciones.

<img decoding="async" src="https://github.com/Roberto-Tierno/Breast_Cancer/blob/main/img/Imagen1.png" alt="Estadísticas de Edad" width="50%">

### Distribución por Resultado de Biopsia: 
El análisis de la distribución de los resultados de biopsia en la población estudiada muestra una clara predominancia del carcinoma ductal, con 220 casos, representando el 92.83% del total. En contraste, el carcinoma lobulillar se presenta en 14 casos (5.91%), evidenciando una menor frecuencia en comparación con el tipo ductal. Adicionalmente, existen 3 casos (1.27%) en los que la información no está disponible. La marcada diferencia en la frecuencia entre ambos tipos sugiere que el carcinoma ductal es la forma más prevalente de cáncer de mama en esta muestra. Para complementar este análisis, se recomienda evaluar la distribución de estos tipos en función de variables adicionales como edad, estadio clínico o factores de riesgo, lo que permitiría una caracterización más detallada de la población afectada.

<img decoding="async" src="https://github.com/Roberto-Tierno/Breast_Cancer/blob/main/img/Imagen2.png" alt="Resultados de Biopsias" width="50%">

### Tiempo de atención desde el inicio de síntomas
El tiempo entre el inicio de los síntomas y la consulta médica presenta una distribución asimétrica a la derecha, con una media de 96.93 días y una mediana de 49 días, lo que indica la influencia de valores extremos. La alta dispersión de los datos, reflejada en una desviación estándar de 142.19 días y un rango de 0 a 973 días, sugiere una variabilidad significativa en el acceso a la atención. El histograma muestra una concentración de casos en tiempos cortos, pero con presencia de valores atípicos que evidencian retrasos excesivos. Este comportamiento resalta la necesidad de analizar factores asociados a estas demoras para mejorar la oportunidad del diagnóstico y tratamiento.

<img decoding="async" src="https://github.com/Roberto-Tierno/Breast_Cancer/blob/main/img/Imagen3.png" alt="Atención desde aparición de síntomas" width="50%">

### Análisis por Tipo de Seguridad Social:  
El análisis de la distribución por tipo de seguridad social muestra un claro predominio del Régimen Contributivo, seguido en menor proporción por el Régimen Subsidiado, mientras que los demás regímenes presentan frecuencias marginales. Esta distribución sugiere una mayor representación de población con empleo formal o capacidad de aporte, lo que podría influir en el acceso y calidad de la atención en salud.

<img decoding="async" src="https://github.com/Roberto-Tierno/Breast_Cancer/blob/main/img/Imagen4.png" alt="Análisis por Tipo de Seguridad Social" width="50%">

### Distribución por Grado Histológico:  
El análisis de la distribución por grado histológico muestra una mayor prevalencia del carcinoma infiltrante, con 154 casos (64.98%), seguido del carcinoma in situ, que representa 58 casos (24.47%), mientras que en 25 casos (10.55%) no se indicó el grado histológico. Esta distribución sugiere que la mayoría de los diagnósticos corresponden a estadios avanzados, lo que podría estar asociado a demoras en la detección temprana. Se recomienda profundizar en el análisis de factores clínicos y sociodemográficos para evaluar su impacto en el diagnóstico oportuno.

<img decoding="async" src="https://github.com/Roberto-Tierno/Breast_Cancer/blob/main/img/Imagen5.png" alt="Distribución por grado histológico" width="50%">

### Distribución por Pertenencia Étnica:  
La distribución por pertenencia étnica muestra un claro predominio de la categoría "Otro" con 230 casos (97.05%), mientras que los grupos afrocolombiano, raizal y rom representan proporciones marginales, con menos del 1% cada uno. Esta concentración sugiere una baja representatividad de poblaciones étnicas específicas en la muestra, lo que limita el análisis de posibles diferencias en el acceso o diagnóstico de la enfermedad según este criterio. Se recomienda evaluar si esta distribución refleja la composición demográfica de la población general o si existen sesgos en la recolección de datos.

<img decoding="async" src="https://github.com/Roberto-Tierno/Breast_Cancer/blob/main/img/Imagen6.png" alt="Distribución por pertenencia étnica" width="50%">

### Distribución de edad por tipo de cáncer: 
Muestra que las medianas de edad son similares tanto para el carcinoma ductal como para el carcinoma lobulillar, con una ligera tendencia a edades más avanzadas en el segundo grupo. La dispersión de los datos es mayor en el carcinoma lobulillar, lo que indica una variabilidad más amplia en la edad de diagnóstico. Además, la mayoría de los casos corresponden al carcinoma ductal (92.83%), seguido por el carcinoma lobulillar (5.91%), con un pequeño porcentaje de datos no disponibles (1.27%). Estos resultados sugieren que, si bien existen diferencias en la edad de presentación, el carcinoma ductal sigue siendo el tipo más frecuente en la muestra analizada.

<img decoding="async" src="https://github.com/Roberto-Tierno/Breast_Cancer/blob/main/img/Imagen7.png" alt="Distribución de edad por tipo de cáncer" width="50%">

### Distribución de casos por grupo etario:
Refleja una mayor concentración en los rangos de 51-60 y 61-70 años, lo que coincide con la edad promedio de diagnóstico del cáncer de mama. Se observa una menor frecuencia en edades tempranas (<40 años), lo que puede estar influenciado por la política de detección temprana en Colombia, que inicia a partir de los 40 años. La tendencia sugiere que la incidencia aumenta progresivamente con la edad hasta los 70 años, tras lo cual disminuye, posiblemente debido a factores de subregistro o menor acceso al diagnóstico en poblaciones de mayor edad.

<img decoding="async" src="https://github.com/Roberto-Tierno/Breast_Cancer/blob/main/img/Imagen8.png" alt="Casos por Grupo Etario" width="50%">

### Distribuciones de Edad en EEUU
La distribución de edad muestra una frecuencia relativamente homogénea entre los 40 y 49 años, con un aumento marcado a partir de los 50 años, lo que sugiere una mayor captación de pacientes en los programas de cribado a esta edad. El pico observado en los 50 años podría estar asociado con la edad de inicio recomendada para mamografías sistemáticas, reflejando la implementación de políticas de detección temprana en E.E.U.U..

<img decoding="async" src="https://github.com/Roberto-Tierno/Breast_Cancer/blob/main/img/Imagen9.png" alt="Distribución de Edad en EEUU" width="50%">

## LIMPIEZA DE DATOS

En cuanto al proceso de limpieza se incluye:  
+ La verificación de valores nulos (no se encontraron),
+ La detección y eliminación de registros duplicados (se encontró 1 duplicado) 
+ No fue necesario realizar imputación de valores faltantes.

## TRANSFORMACIÓN DE DATOS

Se aplicaron varias técnicas de transformación:

+ Codificación  de  variables  categóricas:  Se  usa  One-Hot  Encoding  para variables con múltiples categorías
+ Codificación de la variable objetivo: Se utiliza Label/Encoder para convertir 'Status' (Alive/Dead) en valores binarios (0/1)
+ División de datos: Partición en conjuntos de entrenamiento (80%) y prueba (20%), con estratificación en la variable objetivo
+ Escalado de variables numéricas: Se aplica StandardScaler para normalizar las variables numéricas a media 0 y desviación estándar 1

## CARGA DE DATOS
Al finalizar el proceso, los datasets resultantes se guardan en base de datos en la nube Azure y se sube el código markdown (notebook) al repositorio GitHub. 
Se observan, como muestras, dos capturas de pantalla de los dashboards en Power BI tanto para el Análisis del Cáncer en Colombia como para el Cáncer en Estados Unidos.
<hr>
<img decoding="async" src="https://github.com/Roberto-Tierno/Breast_Cancer/blob/main/img/Dash COL.png" alt="Dashboard de Colombia" width="100%">
<hr>
<img decoding="async" src="https://github.com/Roberto-Tierno/Breast_Cancer/blob/main/img/Dash USA.png" alt="Dashboard de Estados Unidos" width="100%">
<hr>

## ORQUESTACIÓN
Mediante la implementación con AIRFLOW, se cuenta con dos dags/pipelines que orquestan la ejecución de los notebooks de etl , uno para cada notebook de COLAB.

## CONCLUSIONES 
### Características demográficas:

<img decoding="async" src="https://github.com/Roberto-Tierno/Breast_Cancer/blob/main/img/Imagen13.png" alt="Corte a los 40 años" width="100%">

+ La edad media de las pacientes es de aproximadamente  54 años, con un rango de 30 a 69 años
+ Si bien en Colombia se inicia el tamizaje a los 50 años (pico de detección), hay una considerable cantidad de pacientes por debajo de los 30 que justificaría unna intervención de detección a más temprana edad
+ La mayoría de las pacientes registradas son de otras razas, observandose un suregistro de esta clasificación según los valores únicos mostrados
+ Existen diversos estados civiles en la muestra: casadas, divorciadas, solteras, viudas y separadas
### Características clínicas:
+ El tamaño medio del tumor es de 30.47 mm, con un rango amplio (1 mm a 140 mm)
+ La mayoría de los casos presentan receptores de estrógeno y progesterona positivos
+ Se   observan   diferentes   grados   de   diferenciación   tumoral,   desde   bien diferenciados hasta indiferenciados
+ La supervivencia media es de aproximadamente 71 meses (casi 6 años)
### Observaciones importantes:
+ El dataset parece estar bastante completo, sin valores faltantes
+ Hay una variabilidad considerable en el tamaño del tumor y en el número de nódulos linfáticos positivos
+ Se incluyen diferentes etapas de la enfermedad (IIA, IIIA, IIIC, IIB, IIIB)
+ La variable objetivo 'Status' indica si la paciente está viva o ha fallecido
### Limitaciones del análisis:
+ No se realizan análisis de correlación entre variables o modelado predictivo que se realizará en la etapa final.
+  No se menciona el período de tiempo en que se recolectaron estos datos.

## REFERENCIAS
[1] Ministerio de Salud y Protección Social, "Plan Decenal para el Control del Cáncer en Colombia 2012-2021," Bogotá, Colombia, 2012.  
[2] Instituto Nacional de Cancerología, "Análisis de Situación del Cáncer en Colombia 2018," Bogotá, Colombia, 2019.  
[3] G. Hernández et al., "Barreras de acceso a los programas de tamización de cáncer de mama en Colombia," Rev. Salud Pública, vol. 21, no. 3, pp. 372-381, 2019.  
[4] Cuenta de Alto Costo, "Situación del cáncer en la población atendida en el SGSSSde Colombia 2020," Bogotá, Colombia, 2021.  
[5] A. Murillo et al., "Efectividad de los programas de detección temprana de cáncer de mama en América Latina," Rev. Panam. Salud Publica, vol. 30, no. 2, pp. 128-136,2016.  
[6] Ministerio de Salud y Protección Social, "Guía de Práctica Clínica para la detección temprana, tratamiento integral, seguimiento y rehabilitación del cáncer de mama," Bogotá, Colombia, 2017.  
[7] P. López-Alegría et al., "Inequidades en el acceso al diagnóstico temprano del cáncer de mama en Colombia," Biomédica, vol. 38, no. 4, pp. 551-560, 2018.  
[8] World   Health   Organization,   "Guide   to   cancer   early   diagnosis,"   Geneva, Switzerland, 2017.  
[9] R. Aguirre et al., "Costos directos de la atención del cáncer de mama avanzado en comparación con estadios tempranos en Colombia," Rev. Colomb. Cancerol., vol. 22, no. 2, pp. 71-78, 2018.  
[10] F. González-Mariño, "Factores asociados a la detección tardía del cáncer de mama en mujeres colombianas," Univ. Med., vol. 60, no. 1, pp. 41-48, 2019.  
[11] A. Piñeros et al., "Demoras en el diagnóstico y tratamiento de mujeres con cáncer de mama en Bogotá, Colombia," Salud Pública Méx., vol. 53, no. 6, pp. 478-485, 2011.  
[12] O. Bravo et al., "Evaluación económica de la tamización de cáncer de mama con mamografía en diferentes grupos etarios," Rev. Colomb. Cancerol., vol. 20, no. 2, pp. 57-66, 2016.  
[13] Defensoría del Pueblo, "La tutela y el derecho a la salud: Causas de las tutelas en salud," Bogotá, Colombia, 2019.  
[14] Ley 1384 de 2010, "Por la cual se establecen  las acciones para la atención integral del cáncer en Colombia," Congreso de la República de Colombia, 2010.  
[15] GLOBOCAN, "Cancer Today: Data visualization tools for exploring the global cancer burden in 2020," lnternational Agency for Research on Cancer, 2020.  
[16] J. Angarita et al., "Presentación clinicopatológica de mujeres jóvenes con cáncer de mama en Colombia," Rev. Colomb. Cancerol., vol. 23, no. 1, pp. 23-30, 2019.  
[17] M. Velásquez-Fernández et al., "Evaluación de la calidad de las mamografías de tamizaje  en  centros  de  referencia  de  Colombia:  un  estudio  multicéntrico,"  Rev. Colomb. Radiol., vol. 28, no. 4, pp. 4931-4938, 2017.  
[18] F. Rodríguez-Triana et al., "Barreras y facilitadores para la implementación de programas de detección temprana del cáncer de mama en comunidades indígenas y afrodescendientes de Colombia," Cad. Saúde Pública, vol. 36, no. 5, pp. e00114919,2020.  
[19] N. Rincón-Roncancio  et al., "lmplementación  de sistemas  de información  en radiología en Colombia: estado actual y desafíos," Rev. Colomb. Radiol., vol. 31, no.2, pp. 5532-5538, 2020.  
[20]  Superintendencia  Nacional  de  Salud,  "lnforme  de  resultados  del  estudio  de tiempos de espera en la atención en salud en Colombia," Bogotá, Colombia, 2019.  
[21]   The Cancer lmaging Archive(TClA), "Collections,"[Online].   Available: https://www.cancerimagingarchive.net/. [Accessed: 17-Mar-2025].  
[22] University of California lrvine, "Breast Cancer Wisconsin (Diagnostic) Data Set," UCl Machine Learning Repository, 1995. [Online].Available: https://archive.ics.uci.edu/ml/datasets/Breast+Cancer+Wisconsin+(Diagnostic).  Accessed: 17-Mar-2025].  
[23]  National  Cancer  lnstitute,  "The  Cancer  Genome  Atlas  Program,"  GDC  Data Portal, [Online]. Available: https://portal.gdc.cancer.gov/. [Accessed: 17-Mar-2025].  
[24] World Health Organization, "Global Cancer Observatory," lnternational Agency for Research on Cancer, [Online]. Available: https://gco.iarc.fr/. [Accessed: 17-Mar-2025].  
[25]      Kaggle      lnc.,      "Breast      Cancer      Datasets,"      [Online].      Available: https://www.kaggle.com/datasets?search=breast+cancer.  [Accessed: 17-Mar-2025].  
[26] National Cancer Institute, "Surveillance, Epidemiology, and End Results (SEER) Program,"   [Online].   Available:   https://seer.cancer.gov/data/.   [Accessed:   17-Mar-2025].  
[27] J. Ferlay et al., "Global Cancer Observatory: Cancer Today," International Agency for Research on Cancer, Lyon, France, [Online]. Available: https://gco.iarc.fr/today/. [Accessed: 17-Mar-2025].  
[28] Instituto  Nacional  de Cancerología  (INC),  "Datos  Estadísticos,"  Ministerio  de Salud y Protección Social, Colombia, [Online]. Available: https://www.cancer.gov.co/. [Accessed: 17-Mar-2025].  
[29]  Cuenta   de   Alto  Costo,   "Información   Epidemiológica,"   [Online].   Available: https://cuentadealtocosto.org/. [Accessed: 17-Mar-2025].  
[30]  Ministerio  de  Salud  y  Protección  Social,  "Observatorio  Nacional  de  Cáncer Colombia,"[Online].Available: https://www.minsalud.gov.co/salud/publica/PENT/Paginas/Prevenciondel- cancer.aspx. [Accessed: 17-Mar-2025].  
[31]  Departamento  Administrativo  Nacional  de  Estadística  (DANE),  "Estadísticas Vitales," [Online]. Available: https://www.dane.gov.co/. [Accessed: 17-Mar-2025].  
[32] Ministerio de Salud y Protección Social, "Informes de Situación del Cáncer en Colombia,"  [Online].  Available:  https://www.minsalud.gov.co/.  [Accessed:  17-Mar-2025].  
[33] Instituto Nacional de Salud, "Sistema Nacional de Vigilancia en Salud Pública (SIVIGILA)," [Online]. Available: https://www.ins.gov.co/Direcciones/Vigilancia/Paginas/SIVIGILA.aspx. [Accessed: 17-Mar-2025].  
[34] Universidad del Valle, "Registro Poblacional de Cáncer de Cali," [Online]. Available: http://rpcc.univalle.edu.co/. [Accessed: 17-Mar-2025].  
