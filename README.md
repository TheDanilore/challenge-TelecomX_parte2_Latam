# 📊 Análisis de Predicción de Churn en TelecomX


## 🎯 Objetivo del Proyecto
El objetivo principal de este proyecto es **desarrollar modelos predictivos** para identificar a los clientes con mayor probabilidad de cancelar sus servicios (Churn) en la empresa de telecomunicaciones 
ficticia, TelecomX. Al predecir el Churn, la compañía puede implementar estrategias de retención proactivas para reducir la pérdida de clientes.

---

## 📁 Estructura del Repositorio
* `TelecomX_parte2_Latam.ipynb`: Este es el cuaderno principal de Jupyter que contiene todo el proceso de análisis, desde la preparación de los datos hasta la construcción y evaluación del modelo.
* `datos_tratados.csv`: Archivo CSV que contiene el conjunto de datos limpio y procesado, listo para ser utilizado en la fase de modelado.
* `README.md`: Este archivo, que proporciona una visión general del proyecto y su contenido.

---

## Proceso de Preparación y Modelado

### 1. Clasificación de Variables
Se realizó una clasificación de las variables del conjunto de datos en dos tipos principales para su correcto tratamiento:

* **Variables Numéricas**: tenure, MonthlyCharges, TotalCharges.
* **Variables Categóricas**: Todas las demás variables que representan categorías, como gender, Partner, Contract, InternetService, entre otras.
  
### 2. Preprocesamiento de Datos
Antes de modelar, se aplicaron las siguientes transformaciones a los datos:

* **Codificación**: Las variables categóricas se transformaron en un formato numérico que los algoritmos de Machine Learning pudieran entender. Se utilizó la codificación One-Hot Encoding
   para evitar relaciones de orden artificiales.
* **Normalización**: Las variables numéricas se estandarizaron utilizando StandardScaler de Scikit-learn. Esta técnica es crucial para modelos como la Regresión Logística, que son sensibles
   a la escala de las variables, asegurando que ninguna característica domine sobre las otras debido a sus grandes valores.
  
### 3. Separación y Balanceo de Datos
Los datos se dividieron en conjuntos de **entrenamiento (70%)** y **prueba (30%)** para evaluar el rendimiento del modelo en datos no vistos.

Dado que la evasión de clientes (Churn) es un evento minoritario, el conjunto de datos presentaba un desbalance de clases significativo. Para abordar este problema, se aplicó la
técnica **SMOTE (Synthetic Minority Over-sampling Technique)** al conjunto de entrenamiento, lo que generó nuevas instancias de la clase minoritaria (Churn = 1) para equilibrar la distribución.
Esto previene que el modelo se incline a predecir la clase mayoritaria y mejore su capacidad para identificar el Churn.

## Justificación de las Decisiones de Modelado
La elección del modelo de **Regresión Logística** se justifica por su interpretabilidad. Al ser un modelo lineal, sus coeficientes pueden ser analizados para determinar la 
importancia y el impacto de cada variable en la probabilidad de Churn. Esto nos permite obtener información valiosa sobre los factores que impulsan la cancelación, más allá de la simple predicción.

Los resultados del modelo revelaron que las variables más influyentes en el Churn son:

* **Contract_Month-to-month**: El tipo de contrato mes a mes es el predictor más fuerte, lo que indica que los clientes sin un compromiso a largo plazo son los más propensos a irse.
* **tenure**: La antigüedad del cliente. A menor antigüedad, mayor es la probabilidad de Churn. El riesgo es particularmente alto en los primeros meses.
* **InternetService_Fiber optic**: Tener este servicio premium aumenta la probabilidad de Churn, lo que podría sugerir problemas con el precio, la confiabilidad o el soporte técnico.
    
Estos hallazgos clave sirvieron de base para las recomendaciones estratégicas para la retención de clientes.

---

## Visualizaciones e Insights Clave
Durante el Análisis Exploratorio de Datos (EDA) se generaron visualizaciones que proporcionaron insights cruciales:

* **Boxplot de tenure vs Churn**: Este gráfico mostró claramente que los clientes que se van (Churn = 1) tienen una antigüedad significativamente menor que aquellos que se quedan (Churn = 0).
   Esto resalta la importancia de la retención temprana.
  
<img width="686" height="549" alt="image" src="https://github.com/user-attachments/assets/a67902dc-b246-4e34-801f-68a525996156" />

  
* **Boxplot de TotalCharges vs Churn**: La visualización demostró que los clientes que cancelan tienden a tener cargos totales más bajos, lo cual es consistente con una menor tenencia.
  Refuerza la idea de que los clientes que se van no han llegado a generar un alto valor a lo largo del tiempo (Lifetime Value).

<img width="704" height="549" alt="image" src="https://github.com/user-attachments/assets/6359efd6-850a-4761-bf41-0b16f081fa60" />

* **Matrices de Confusión de los modelos de Regresión Logística y Random Forest** Este gráfico compara el desempeño de dos modelos de clasificación en la predicción de churn. La Regresión
   Logística logró identificar a más clientes que efectivamente abandonaron (TP = 299 vs 263), mientras que el Random Forest presentó mayor cantidad de falsos negativos. Ambos modelos
   muestran un desempeño similar en la clasificación de clientes que no hicieron churn. 

<img width="1286" height="549" alt="image" src="https://github.com/user-attachments/assets/c463341e-eaf1-4456-b8fc-b34536a03f9c" />


---

## 🚀 Cómo Ejecutar el Notebook
Para ejecutar el análisis completo, sigue estos pasos:

1.  Abre el archivo `TelecomX_parte2_Latam.ipynb` en un entorno como **Google Colab**.
2.  Sube el archivo de `datos_tratados.csv`.
3.  Ejecuta cada celda del notebook secuencialmente.
4.  Al final del notebook, encontrarás las conclusiones.

---

**Desarrollado por**: TheDanilore

**Tecnologías Utilizadas**:
* Python
* Pandas (para manipulación de datos)
* Matplotlib (para visualización de datos)
* seaborn (para crear visualizaciones estadísticas atractivas)
* Numpy (manipulación y procesamiento de datos numéricos)
* Scikit-learn (Creacion y entrenamiento de modelos)
* Google Colab
