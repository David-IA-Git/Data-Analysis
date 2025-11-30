# Data Analysis
Análisis de datos para predecir el riesgo de abandono (churn) de clientes con PyTorch y Power BI.


[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1bP8ErHroxyGwo1DSJkgMVhf3WCgn6_30?usp=sharing)
> **Nota:** Haz clic en el botón de arriba para abrir el notebook directamente en Google Colab.

---

## Resumen del Proyecto

Este proyecto aborda el problema crítico de la **Predicción de Abandono (Churn)** de clientes en la industria de telecomunicaciones. Combina la precisión de los modelos de **Deep Learning** (implementados con PyTorch) con la claridad y el impacto de la **Inteligencia de Negocio (Power BI)** para generar información práctica.

El objetivo principal fue desarrollar un modelo capaz de **identificar proactivamente** a los clientes con alto riesgo de abandono, permitiendo intervenciones de retención dirigidas.

## Tecnologías Utilizadas

| Categoría | Herramienta | Uso Principal |
| :--- | :--- | :--- |
| **Deep Learning** | **PyTorch** | Construcción, entrenamiento y validación de la Red Neuronal Feedforward (FFNN). |
| **Análisis de Datos** | **Pandas, NumPy, Scikit-learn** | Carga, limpieza, pre-procesamiento, escalado (MinMaxScaler) y métricas de evaluación. |
| **Visualización/BI** | **Power BI** | Exploración inicial de datos, análisis de factores de riesgo, y visualización final de las métricas de rendimiento y la matriz de confusión. |
| **Dataset** | **Telco Customer Churn** | Conjunto de datos estándar de Kaggle para la modelización de Churn. |

---

## Arquitectura del Modelo (PyTorch)

* **Tipo de Modelo:** Red Neuronal Feedforward (FFNN).
* **Capas:** 5 capas densas con activación **ReLU**.
* **Regularización:** Alta tasa de **Dropout (0.6)** en cada capa oculta para prevenir el sobreajuste.
* **Optimización:** Optimizador **Adam** con función de pérdida **`BCEWithLogitsLoss`** (ideal para clasificación binaria).
* **Estrategia de Entrenamiento:** Se implementó **Early Stopping** con paciencia de 20 épocas, guardando el mejor modelo basado en la métrica **Val Accuracy**.

## Resultados y Análisis de Negocio

El enfoque del proyecto se centró en la **Retención de Clientes**, por lo que la métrica más importante fue el **Recall (Verdaderos Positivos)** para la clase 'Churn (1)'.

| Métrica | Umbral (0.5) Inicial | Umbral (0.4) Optimizado | Impacto del umbral (0.4) |
| :--- | :--- | :--- | :--- |
| **Recall (Clase Churn)** | ~0.63 | **~0.74** | **Incremento del 11%** en la detección de clientes en riesgo. |
| **Accuracy General** | ~0.80 | **~0.75** | Ligera disminución, aceptada para priorizar la detección de riesgo. |

### Conclusión Estratégica
El **ajuste del umbral de clasificación de 0.5 a 0.4** fue clave. Aunque redujo ligeramente la precisión general, elevó el **Recall de Churn al 74%**, lo que significa que el modelo ahora identifica correctamente a **7 de cada 10 clientes que realmente rotarán**. Esto maximiza el potencial de la empresa para aplicar ofertas de retención a los clientes correctos.

### Power BI
El análisis de datos con Power BI identificó los principales impulsores de riesgo:

* **Tipo de Contrato:** El contrato **Mes a Mes** es un factor de riesgo muy alto.
* **Coste/Antigüedad:** Los clientes con **cargos mensuales altos** (entre $80 y $110) tienen una alta probabilidad de Churn, incluso aquellos con alta antigüedad (`Tenure`), lo que sugiere un problema de valor percibido.
