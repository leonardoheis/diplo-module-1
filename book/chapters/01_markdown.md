---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
    format_version: '0.8'
    jupytext_version: '1.4.1'

kernelspec:
  display_name: Python 3
  name: python3
---

# Trabajo Práctico Final
### Machine Learning & Deep Learning

### 1. Objetivo

Aplicar las técnicas vistas en la diplomatura a un problema real de datos, recorriendo el ciclo completo: exploración, preprocesamiento, entrenamiento de modelos y evaluación crítica de resultados.

### 2. Consigna

#### Dataset

Utilizar un dataset propio del entorno laboral (recomendado) o uno de los datasets de ejemplo de la Sección 4.

#### Modelos a entrenar

Entrenar al menos dos modelos sobre el mismo dataset, aplicados al mismo problema:
- Un modelo de ML clásico: Regresión Lineal/Logística, Decision Tree, XGBoost, Random Forest, u otro justificado.
- Una Red Neuronal: con TensorFlow o PyTorch.
Esto permite comparar directamente un enfoque clásico contra uno de Deep Learning.

### 3. Estructura Sugerida del Informe

#### 3.1. Introducción
Describir el dataset (origen, qué representa cada fila/columna), definir la variable objetivo y el tipo de problema (clasificación o regresión).

#### 3.2. Análisis Exploratorio (EDA)
Estadísticas descriptivas, visualizaciones clave (histogramas, correlaciones, distribución de clases) e identificación de problemas como desbalanceo, outliers o datos faltantes.
Usar la librería ydata_profiling para el EDA.

#### 3.3. Preprocesamiento
Tratamiento de nulos y outliers, encoding de categóricas, normalización, split train/test y técnicas de balanceo si corresponde.

#### 3.4. Entrenamiento
Modelo de ML: justificar la elección del algoritmo y describir hiperparámetros y proceso de tuning.

#### 3.5. Evaluación y Comparación
Esta es la sección más importante. No alcanza con reportar un número de accuracy.
Para clasificación, incluir: accuracy, precision, recall, F1-score, y matriz de confusión (obligatoria para ambos modelos). Curva ROC/AUC es opcional pero valorada.
Para regresión: MAE, RMSE, R², y gráfico de predicciones vs. valores reales.
El análisis crítico debe abordar:
- ¿Cuál modelo performó mejor y por qué?
- ¿La red neuronal superó al ML clásico? ¿Era esperable dado el dataset?
- ¿Hay indicios de overfitting? ¿Cómo se detecta y mitiga?
- ¿Qué features resultaron más relevantes?
- ¿Qué se mejoraría con más tiempo o más datos?

#### 3.6. Conclusiones
Síntesis de resultados, lecciones aprendidas y posibles líneas de trabajo futuro.


### 4. Datasets de Ejemplo
Para quienes no dispongan de un dataset laboral, se proponen estas tres opciones de código abierto:

#### 4.1. Telco Customer Churn (Clasificación)

| Campo      | Detalle                                                        |
|------------|----------------------------------------------------------------|
| Fuente     | IBM Sample Datasets / Kaggle                                   |
| Registros  | 7.043 clientes                                                 |
| Features   | 21 columnas: demográficas, de servicio y de facturación        |
| Target     | Churn (Sí/No)                                                  |
| Descarga   | [kaggle.com/datasets/blastchar/telco-customer-churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) |

Interés: problema clásico de negocio. Desbalanceo moderado (~26% churn) que obliga a ir más allá del accuracy. Mix de variables categóricas y numéricas.

#### 4.2. Heart Disease (Clasificación)

| Campo      | Detalle                                                        |
|------------|----------------------------------------------------------------|
| Fuente     | UCI Machine Learning Repository                                |
| Registros  | 303 pacientes                                                   |
| Features   | 14 columnas: demográficas, análisis de sangre y test de esfuerzo |
| Target     | Heart Disease (Sí/No)                                          |
| Descarga   | [archive.ics.uci.edu/dataset/45/heart+disease](https://archive.ics.uci.edu/dataset/45/heart+disease) |

Interés: dataset pequeño donde el recall importa más que la precision (contexto médico). Fuerza la discusión sobre overfitting y sobre por qué un modelo simple puede ganarle a una red neuronal con pocos datos.

#### 4.3. California Housing (Regresión)

| Campo      | Detalle                                                        |
|------------|----------------------------------------------------------------|
| Fuente     | UC Irvine Machine Learning Repository                          |
| Registros  | 20.640 casas                                                     |
| Features   | 8 columnas: características de la casa y barrio                  |
| Target     | Precio medio de la casa (USD)                                    |
| Descarga   | from sklearn.datasets import fetch_california_housing |

Interés: dataset de referencia para regresión. Suficientes datos para que la red neuronal aporte valor. Permite explorar feature engineering geoespacial y usar métricas distintas (MAE, RMSE, R²).