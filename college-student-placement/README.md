# 🎓 🎓 ¿Qué factores podrían influir en la colocación laboral de estudiantes universitarios?

Este proyecto es un ejercicio práctico de ciencia de datos en el que se entrena un modelo de clasificación para predecir si un estudiante será colocado laboralmente (`Placement`), utilizando un **dataset de prueba** con características académicas, habilidades y experiencia.

## 🧠 Objetivo

Explorar el potencial de modelos simples e interpretables como los árboles de decisión para predecir colocación laboral, reforzando buenas prácticas de análisis exploratorio, validación cruzada y evaluación de modelos.

---

## 📦 Dataset

El dataset simulado contiene las siguientes variables para cada estudiante:

- `IQ` – Coeficiente Intelectual
- `Prev_Sem_Result` – Promedio del semestre anterior
- `CGPA` – Nota media acumulada
- `Academic_Performance` – Evaluación del rendimiento académico
- `Internship_Experience` – ¿Tiene experiencia en prácticas? (Sí/No)
- `Extra_Curricular_Score` – Participación en actividades extracurriculares
- `Communication_Skills` – Habilidad de comunicación (1-10)
- `Projects_Completed` – Número de proyectos completados
- `Placement` – Variable objetivo (Sí/No)

> ⚠️ **Nota**: Este es un *toy dataset* (simulado) utilizado con fines didácticos.

---

## 🔎 Exploración de Datos

Se realizó un análisis gráfico de densidades para visualizar cómo se distribuyen las variables predictoras según el estado de colocación (`Placement`). Las variables con mayor capacidad discriminativa fueron:

- `Communication_Skills`
- `CGPA`

Estas se reflejan como los principales nodos del árbol estimado.

---

## 🌳 Modelado

Se entrenó un **Árbol de Decisión** con ajuste de hiperparámetros mediante `GridSearchCV`, variando `max_depth` desde 2 hasta `log2(n)` con validación cruzada (CV=5).

📌 Se calcularon intervalos de confianza del 95% (aprox.) para los valores de accuracy medios (t-Student).

---

## 📈 Mejor modelo encontrado: max_depth = 2

- Accuracy: 90%

- IC del 95% : [ 87.1% ; 92.07%]

- AUC: 0.872



Árbol simple y explicable: solo usa Communication_Skills y CGPA

Matriz de confusión mostró un alto desempeño en la clase negativa, pero menor recall para los positivos (colocados). Lo esperable debida a su distribución en la muestra:


Placement

No     8341

Yes    1659


Matriz de Confusión 
 [[2420   94]
 [ 206  280]]

---

## ✅ Conclusión

Este ejercicio demuestra cómo, incluso con un dataset de prueba, se pueden aplicar buenas prácticas de ciencia de datos para construir modelos simples, interpretables y eficaces. 

