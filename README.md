# TFG_NLP_Sentiment_Analysis
Repositorio oficial del TFG: Evaluación comparativa de modelos de lenguaje (BERT y GPT) en análisis de sentimiento. Universitat Oberta de Catalunya (UOC) - Semestre 2025-1.

# Evaluación comparativa de modelos de lenguaje (BERT, GPT, LLaMA) en análisis de sentimiento y sesgos

Este repositorio contiene el código fuente, los scripts de experimentación y los resultados de auditoría correspondientes al Trabajo de Fin de Grado (TFG) del Grado en Ingeniería Informática (UOC).

## Descripción del proyecto
El proyecto evalúa la eficacia, robustez y ética de tres paradigmas arquitectónicos de NLP aplicados al análisis de sentimiento en reseñas de clientes (IMDb, Amazon, Yelp):
1.  **BERT (encoder):** Enfoque discriminativo clásico.
2.  **GPT-2 (decoder):** Enfoque generativo base (re-entrenado para clasificación).
3.  **TinyLlama (LLM):** Enfoque generativo moderno optimizado con LoRA y Cuantización.

El estudio incluye una evaluación de transferencia de aprendizaje (*cross-domain transfer*) y una auditoría de equidad algorítmica y mitigación de sesgos (CDA).

## Estructura del Repositorio
El código se divide en 5 notebooks modulares que deben ejecutarse secuencialmente:

| Orden | Archivo | Descripción |
| :--- | :--- | :--- |
| **01** | `Preprocesamiento.ipynb` | Pipeline ETL. Limpieza regex, fusión de características y submuestreo estratificado (N=50k). |
| **02** | `Implementacion_inicial.ipynb` | *Smoke Test*. Validación de carga de modelos y baseline Zero-Shot. |
| **03** | `Implementacion_completa.ipynb` | **Entrenamiento Maestro**. Fine-tuning de BERT/GPT-2 y QLoRA (4-bits) para TinyLlama. |
| **04** | `Evaluacion_transferencia.ipynb` | Validación cruzada. Evalúa los modelos en dominios no vistos (Amazon/Yelp). |
| **05** | `Implementacion_explicabilidad_sesgo.ipynb` | Auditoría Ética. Análisis SHAP/LIME y algoritmo de mitigación (CDA). |

Nota: Se recomienda descargar los archivos para su visualización por errores de compatibilidad de los metadatos de Colab

## Requisitos de ejecución

### Hardware recomendado
Debido al uso de LLMs y técnicas de cuantización, se requiere aceleración por GPU.
* **Mínimo:** NVIDIA T4 (16GB VRAM) - *Solo para inferencia o BERT.*
* **Recomendado (el usado en TFG):** **NVIDIA A100 (40GB VRAM)** - *Necesario para el entrenamiento QLoRA de TinyLlama y validación masiva.*

### Instalación de dependencias
Para reproducir el entorno, instale las dependencias listadas:

```bash
pip install -r requirements.txt
