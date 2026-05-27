# Software Monetization Impact Tracker (NLP & Sentiment Analysis)

Este proyecto desarrolla un pipeline analítico de **Procesamiento de Lenguaje Natural (NLP)** diseñado para auditar de forma automatizada cómo las decisiones de monetización y diseño de producto afectan la percepción del consumidor. 

Al transformar cientos de miles de reseñas de software no estructuradas en métricas cuantificables, este modelo extrae inteligencia de negocios accionable, superando las limitaciones de los sistemas de calificación tradicionales (promedio de estrellas).

## Arquitectura del Proyecto

El análisis se dividió en 4 fases ejecutadas secuencialmente en un entorno de Google Colab:

1. **Ingesta y Preprocesamiento (NLP):**
   * Descarga automatizada desde la nube utilizando `gdown` para garantizar reproducibilidad sin fricción.
   * Limpieza de texto mediante Expresiones Regulares (Regex).
   * Reducción de dimensionalidad aplicando eliminación de *Stop Words* y Lematización con la librería `NLTK`.

2. **Análisis de Sentimiento (Lexicon-Based):**
   * Implementación de **VADER** (*Valence Aware Dictionary and sEntiment Reasoner*).
   * Evaluación de polaridad y cálculo del impacto emocional real (score compuesto de -1.0 a 1.0) evaluando el sarcasmo y la intensidad basada en puntuación.

3. **Modelado de Temas (Topic Modeling) y Disonancia Cognitiva:**
   * Extracción de N-gramas (Bigramas) con `CountVectorizer` sobre el espectro de sentimiento negativo para agrupar automáticamente los motivos de queja.
   * Cruce paramétrico entre la calificación nominal (Estrellas) y el sentimiento analítico (VADER) mediante visualizaciones de caja (Boxplots) con `seaborn`.

4. **Insights de Negocio:**
   * Traducción de las anomalías estadísticas en reportes de riesgo de abandono (*churn*) y erosión de lealtad en la base de usuarios instalada.

## Hallazgos Principales

* **Fricción por Monetización ("waste money"):** Existe un rechazo directo y cuantificable hacia la implementación agresiva de muros de pago, que los usuarios no consideran justificados por el valor del software.
* **La Ilusión del Promedio de Estrellas:** El análisis de disonancia cognitiva comprobó la existencia de *outliers* críticos: usuarios otorgando 4 o 5 estrellas mientras reportan fallos severos o quejas en el texto. Depender exclusivamente de las estrellas oculta el descontento real.
* **Erosión de la Lealtad ("update app", "used love"):** El mayor riesgo detectado proviene de usuarios veteranos que resienten actualizaciones recientes, subrayando que los cambios abruptos en el ecosistema destruyen la confianza acumulada.

## Stack Tecnológico

* **Lenguaje:** Python 3
* **Entorno:** Google Colab / Jupyter Notebook
* **Procesamiento de Datos:** Pandas, Regex, Scikit-Learn
* **Natural Language Processing (NLP):** NLTK (VADER, WordNetLemmatizer)
* **Visualización de Datos:** Matplotlib, Seaborn

## Cómo ejecutar este proyecto

Este proyecto fue diseñado con una filosofía de "fricción cero". No necesitas descargar datasets manualmente ni configurar variables de entorno locales.

1. Clona este repositorio:
   ```bash
   git clone [https://github.com/tu-usuario/Software-Monetization-Impact-Tracker.git](https://github.com/tu-usuario/Software-Monetization-Impact-Tracker.git)
