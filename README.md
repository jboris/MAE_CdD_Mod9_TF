## 📄 README: Clasificación de Sentimiento en Reseñas de Películas en Español con BETO

***

### 🎯 Descripción del Proyecto

Este proyecto consiste en la implementación de un modelo de **Clasificación de Sentimiento Binario** (Positivo/Negativo) aplicado a un conjunto de reseñas de películas en español. El objetivo principal es evaluar la eficacia de la técnica de **Fine-Tuning** (ajuste fino) sobre el modelo pre-entrenado **BETO** (BERT en español) para tareas de Procesamiento de Lenguaje Natural (PLN) en el contexto hispanohablante.

El desarrollo completo y la ejecución del modelo se realizan en un entorno de **Google Colaboratory**.

***

### ⚙️ Metodología

#### 1. Fuente de Datos
Se utilizó el **IMDb Dataset of 50k Movie Reviews (Spanish)**, obtenido de la plataforma Kaggle. El conjunto de datos original contenía un desbalance considerable entre las clases de sentimiento.

#### 2. Preprocesamiento y Balanceo de Datos
* **Análisis de Desbalance:** Se identificó un desbalance de clases inicial con más reseñas clasificadas como "positivo" (6057) que como "negativo" (2808).
* **Estrategia de Balanceo:** Se aplicó la técnica de **Submuestreo** (*Undersampling*) a la clase mayoritaria ("positivo") para igualar su número de muestras al de la clase minoritaria ("negativo"). El conjunto de datos balanceado resultante fue de **5616 muestras** (2808 de cada clase).

#### 3. Modelo de PLN (BETO)
Se empleó la arquitectura **BERT** (Bidirectional Encoder Representations from Transformers), específicamente la versión pre-entrenada para el idioma español: **BETO** (`dccuchile/bert-base-spanish-wwm-cased`).

El modelo fue ajustado (fine-tuned) para la tarea de **clasificación de secuencia** utilizando la librería `transformers` de Hugging Face.

#### 4. Entrenamiento y Evaluación
El modelo fue entrenado utilizando el *Trainer* de la librería `transformers` durante 2 épocas.

***

### 📊 Resultados

El modelo de clasificación de sentimiento alcanzó los siguientes resultados en el conjunto de evaluación:

| Métrica | Valor |
| :--- | :--- |
| **Pérdida de Validación** (*Validation Loss*) | 0.4348 |
| **Precisión Global** (*Accuracy*) | **0.880** (88.0%) |
| **AUC (Área Bajo la Curva ROC)** | **0.88** |

#### Reporte de Clasificación Detallado:

| Clase | Precisión (*Precision*) | Recuperación (*Recall*) | Puntuación F1 (*F1-Score*) |
| :--- | :--- | :--- | :--- |
| **negativo** | 0.90 | 0.86 | 0.88 |
| **positivo** | 0.87 | 0.90 | 0.88 |

Los resultados demuestran un rendimiento robusto con una alta precisión, indicando que el modelo BETO, tras el ajuste fino, es altamente efectivo para la clasificación de sentimiento en reseñas de películas en español.

***

### 💻 Requisitos y Ejecución

Para reproducir este proyecto, es necesario un entorno que soporte la ejecución de notebooks de Jupyter/Colab y las siguientes librerías:

#### Librerías Principales:
* `transformers`
* `datasets`
* `opendatasets`
* `pandas`, `numpy`, `matplotlib`, `seaborn`, `sklearn` (para métricas)

**Nota:** Se recomienda el uso de un entorno de ejecución con **GPU** (como la T4 utilizada en el proyecto) debido a los altos requerimientos computacionales del modelo BERT.

#### Pasos de Ejecución (en Google Colab):
1.  **Instalar dependencias:** Ejecutar las celdas que instalan `transformers` y `datasets`.
2.  **Descargar datos:** Ejecutar la celda de `od.download(dataset_url)` e introducir las credenciales de Kaggle cuando se solicite.
3.  **Ejecutar el *Notebook*:** Seguir secuencialmente las celdas para la carga, preprocesamiento de datos, configuración del modelo BETO, entrenamiento, y finalmente la evaluación de resultados.
