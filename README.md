# Clasificación de humor en textos cortos con modelos estadísticos

Este proyecto tiene como objetivo analizar y predecir si un texto corto es humorístico o no, utilizando técnicas de procesamiento de lenguaje natural (NLP) y modelos estadísticos clásicos de clasificación.

---

## Dataset

Se utilizó el dataset [200K Short Texts for Humor Detection](https://www.kaggle.com/datasets/deepcontractor/200k-short-texts-for-humor-detection) disponible en Kaggle. Contiene 200 000 textos cortos en inglés etiquetados como `humor=True` o `humor=False`.

- **Variables clave:**
  - `text`: contenido del texto.
  - `humor`: variable binaria que indica si el texto es humorístico (`True`) o no (`False`).

---

## Objetivos

1. Realizar un análisis exploratorio del lenguaje humorístico.
2. Preprocesar los textos y aplicar técnicas de vectorización (TF-IDF).
3. Entrenar y evaluar distintos modelos de clasificación:
   - Regresión logística
   - Naive Bayes
   - Random Forest
4. Comparar su rendimiento con métricas como accuracy, matriz de confusión y curvas de aprendizaje.
5. Extraer conclusiones sobre el comportamiento lingüístico del humor.

---

## Preprocesamiento y vectorización

- Se eliminaron caracteres no alfabéticos y se normalizó el texto (minúsculas, sin acentos).
- Se eliminaron los números, por considerarse poco informativos para este caso.
- Se aplicó `TfidfVectorizer` para convertir los textos en vectores numéricos. Se probó con distintos tamaños del vocabulario (`max_features=50`, `15000`, etc.). Se probó también eliminar los stopwords, y se optó por no hacerlo de acuerdo con la precisión observada.

---

## Modelos implementados

### 1. Regresión logística
Modelo lineal que predice la probabilidad de que un texto sea humorístico a partir de los valores TF-IDF de sus palabras.

### 2. Naive Bayes (MultinomialNB)
Clasificador probabilístico basado en el teorema de Bayes, que asume independencia entre palabras. Funciona sorprendentemente bien en tareas de clasificación de texto.

### 3. Random Forest
Modelo de conjunto basado en árboles de decisión. Fue probado con una versión reducida del vocabulario debido a limitaciones computacionales.

---

## Evaluación y resultados

Se usaron métricas estándar para evaluar el rendimiento. Se presentan los resultados del modelo de regresión logística:

- **Accuracy general** del modelo: ~0.94
- **Precision y Recall**:
  - Textos humorísticos: ~94%
  - Textos no humorísticos: ~95%
- Las **curvas de aprendizaje** mostraron un buen comportamiento en todos los modelos, con mejoras consistentes a medida que aumentaba el tamaño del conjunto de entrenamiento.

---

## Conclusiones

- El modelo de regresión logística ofreció el mejor rendimiento general, aunque Naive Bayes lo siguió muy de cerca.
- Random Forest tuvo un rendimiento competitivo, pero fue computacionalmente más costoso.
- El uso de preprocesamiento ayudó a reducir el ruido y mejorar la generalización.
- El humor parece tener una estructura lingüística recurrente, lo que facilitó su detección mediante modelos estadísticos clásicos.

---

## Archivos incluidos

- `dataset.csv`: dataset original.
- `dataset (b).csv`: dataset procesado con columnas añadidas.
- `Análisis exploratorio profundo del humor textual.ipynb`: análisis exploratorio, frecuencias y visualización.
- `Modelos estadísticos para predecir si un texto es humorístico.ipynb`: vectorización y clasificación.

---

