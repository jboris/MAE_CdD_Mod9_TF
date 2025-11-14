## 📄 README: Clasificación de Sentimiento en Reseñas de Películas en Español con BETO

***

### 🎯 Descripción del Proyecto

Este proyecto consiste en la implementación de un modelo de **Clasificación de Sentimiento Binario** (Positivo/Negativo) aplicado a un conjunto de reseñas de películas en español. El objetivo principal es clasificar la percepción del público sobre las películas exhibidas en un cine, utilizando un modelo inteligente para procesar y evaluar los comentarios publicados por los usuarios en redes sociales.

El desarrollo completo y la ejecución del modelo se realizan en un entorno de **Google Colaboratory**.

***

### ⚙️ Metodología

#### 1. Fuente de Datos

Se utilizaron los siguientes datos:

| Nombre                                                         | Descripción                                                                                           |
| -------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| Críticas de películas Filmaffinity en Español (Moya, 2021).    | Contiene críticas de usuarios de Filmaffinity sobre más de 50 películas españolas.                    |
| Críticas Filmaffinity Netflix Español (Mos, 2024).             | Incluye críticas de usuarios de Filmaffinity sobre todas las películas y series españolas en Netflix. |
| IMDB Dataset of 50K Movie Reviews (Spanish) (Fernandez, 2021). | Basado en el conjunto de datos de 50,000 reseñas de películas de IMDB, adaptado al español.           |

#### 2. Preprocesamiento y Balanceo de Datos

De cada dataset se obtubieron datos en la misma cantidad de comentarios positivos y negativos, obteniendo un dataset set final de:

* positivo: 30255.

* negativo: 30255.

#### 3. Modelo de PLN (BETO)

Se empleó la arquitectura **BERT** (Bidirectional Encoder Representations from Transformers), específicamente la versión pre-entrenada para el idioma español: **BETO** (`dccuchile/bert-base-spanish-wwm-cased`).

El modelo fue ajustado (fine-tuned) para la tarea de **clasificación de secuencia** utilizando la librería `transformers` de Hugging Face.

#### 4. Entrenamiento y Evaluación

El modelo fue entrenado utilizando el *Trainer* de la librería `transformers` durante 2 épocas.

***

### 📊 Resultados

El modelo de clasificación de sentimiento alcanzó los siguientes resultados en el conjunto de evaluación:

| Métrica                                       | Valor             |
|:--------------------------------------------- |:----------------- |
| **Pérdida de Validación** (*Validation Loss*) | 0.4348            |
| **Precisión Global** (*Accuracy*)             | **0.880** (88.0%) |
| **AUC (Área Bajo la Curva ROC)**              | **0.88**          |

#### Reporte de Clasificación Detallado:

| Clase        | Precisión (*Precision*) | Recuperación (*Recall*) | Puntuación F1 (*F1-Score*) |
|:------------ |:----------------------- |:----------------------- |:-------------------------- |
| **negativo** | 0.90                    | 0.86                    | 0.88                       |
| **positivo** | 0.87                    | 0.90                    | 0.88                       |

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

1. **Instalar dependencias:** Ejecutar las celdas que instalan `transformers` y `datasets`.
2. **Descargar datos:** Ejecutar la celda de `od.download(dataset_url)` e introducir las credenciales de Kaggle cuando se solicite.
3. **NLP*:** Carga y preprocesamiento de datos, configuración del modelo BETO, entrenamiento, y finalmente la evaluación de resultados.
