# Clasificación de Cáncer de Mama con Árboles de Decisión y AdaBoost

Este ejercicio consiste en entrenar modelos de clasificación utilizando la base de datos de **Breast Cancer Wisconsin**, con el objetivo de predecir si un tumor es maligno o benigno.

---

## 📊 Variable dependiente: `diagnosis`

La variable objetivo (`diagnosis`) contiene dos clases:

- **B (Benigno)**: 62.7%
- **M (Maligno)**: 37.3%

Esto indica una distribución moderadamente desbalanceada, por lo que se presta atención especial a métricas adicionales más allá del accuracy.

---

## 🔍 Desarrollo

### 1. Árbol de Decisión

- Se entrenó un modelo de árbol de decisión ajustando el hiperparámetro `max_depth` mediante validación cruzada con `GridSearchCV`.
- El mejor resultado se obtuvo con `max_depth = 4`, alcanzando un **94% de accuracy en el conjunto de test**.

### 2. Intervalo de Confianza

- Se calculó un intervalo de confianza para el `mean_test_score` de cada profundidad (`max_depth`).
- El intervalo para `max_depth = 2` incluía el mejor accuracy logrado con `max_depth = 4`, lo que sugiere que el modelo más simple podría ser igualmente válido.

### 3. AdaBoost

- Se entrenó un clasificador **AdaBoost** usando como estimador base un árbol de decisión con `max_depth = 2`.
- Se exploraron distintos valores para `n_estimators` mediante grid search.
- El mejor resultado se obtuvo con **20 estimadores**, logrando un **99% de accuracy en el conjunto de test**.

---

## 🧪 Métricas del modelo AdaBoost (con `max_depth = 2`, `n_estimators = 20`)

**Accuracy en test**: `0.9941`

### 📁 Matriz de confusión

Predicciones en columnas, reales en filas

| B  | M | X |
|----|---|---|
|108 | 0 | B |
| 1  | 62| M |




### 📄 Classification Report

| Clase | Precision | Recall | F1-score | Support |
|-------|-----------|--------|----------|---------|
| B     | 0.99      | 1.00   | 1.00     | 108     |
| M     | 1.00      | 0.98   | 0.99     | 63      |

- **Accuracy global**: 99%
- **Macro promedio**: F1 = 0.99
- **Promedio ponderado**: F1 = 0.99

---

## ✅ Conclusión

El uso de AdaBoost con clasificadores base simples permite mejorar significativamente el rendimiento del modelo. A pesar del uso de árboles de baja profundidad, se alcanzó un 99% de precisión en test. Además, el análisis de intervalos de confianza permitió justificar el uso de modelos más simples sin pérdida significativa de rendimiento.
