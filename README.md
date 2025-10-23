# Análisis de Expresión Génica – Clasificación de Tipos de Cáncer

Este proyecto aplica métodos estadísticos y modelos de aprendizaje automático (SVM) para analizar un conjunto de datos de expresión génica estandarizada.  
El objetivo es identificar genes con diferencias significativas entre distintos tipos de cáncer y construir modelos predictivos que clasifiquen correctamente las muestras según su tipo.

---

## Archivos del repositorio

| Archivo | Descripción |
|----------|--------------|
| [`Khan_Cancer.csv`](./Khan.csv) | Base de datos con 83 muestras y 2308 genes estandarizados. La variable `y` indica el tipo de cáncer (1–4). |
| [`Khan_Cancer.ipynb`](./Khan_Cancer.ipynb) | Notebook principal con el desarrollo completo del análisis, dividido por incisos (1–5). Incluye pruebas estadísticas, visualizaciones y modelos SVM. |
| [`Khan_Cancer.html`](./Khan_Cancer.html) | Versión exportada del notebook para visualización rápida sin entorno Jupyter. |

---

## Contenido del análisis

### Inciso 1 – Exploración de datos
- Carga y revisión del dataset.  
- Verificación de valores faltantes.  
- Cálculo de diferencias de medias entre clases 2 y 4.  
- Identificación de los 10 genes con mayor variación.

### Inciso 2 – Prueba t y correcciones múltiples
- Comparación estadística entre las clases 2 y 4 mediante *t-test* independiente.  
- Aplicación de correcciones por comparaciones múltiples: Bonferroni, Holm y Benjamini–Hochberg (FDR).  
- Identificación de genes con diferencias significativas en la expresión.

### Inciso 3 – ANOVA entre las cuatro clases
- Análisis de varianza de una vía (ANOVA) para los 4 tipos de cáncer.  
- Corrección FDR mediante Benjamini–Hochberg.  
- Identificación de los genes con mayor variabilidad entre clases.

### Inciso 4 – Modelado con SVM
- Selección de los 50 genes más significativos del ANOVA.  
- División de los datos en entrenamiento (70%) y prueba (30%) de forma estratificada.  
- Entrenamiento de tres modelos SVM: Lineal, Polinomial (grado 3) y Radial (RBF).  
- Evaluación del desempeño mediante *accuracy*, *precision*, *recall* y *F1-score*.  
- Visualización de matrices de confusión directamente en el notebook.

### Inciso 5 – Comparación de modelos
- Comparación global de métricas.  
- Selección del mejor kernel para la clasificación de tipos de cáncer.  
- Interpretación de resultados.

---

## Resultados principales

- Genes significativos:  
  - *t-test (2 vs 4):* 296 genes con FDR < 0.05  
  - *ANOVA (4 clases):* 1162 genes con FDR < 0.05  
- Modelos SVM:  
  - SVM Lineal: Accuracy = 1.00  
  - SVM RBF: Accuracy = 1.00  
  - SVM Polinomial (grado 3): Accuracy = 0.92  
- Conclusión:  
  Los modelos SVM Lineal y RBF logran una clasificación perfecta.  
  Dado el bajo costo computacional, el SVM Lineal se considera el modelo más adecuado.

---

## Tecnologías utilizadas

- Python 3.10+  
- Bibliotecas principales:  
  pandas, numpy, scipy, statsmodels, scikit-learn, matplotlib
