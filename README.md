# 📉 Telecom X parte 2 Predicción de Cancelación de Clientes (Churn) - 


## 📌 Descripción del Proyecto
Objetivo: construir modelos predictivos de Machine Learning para ayudar a la empresa de telecomunicaciones **Telecom X** a anticipar la evasión de clientes (Churn). 

Este proyecto se enfoca en identificar proactivamente a los usuarios en riesgo de cancelar sus servicios, descubrir las variables clave que impulsan esta decisión y proponer estrategias de retención basadas en datos.

* **Identificar clientes en riesgo:** Predecir con alta sensibilidad (Recall) qué clientes están a punto de abandonar la empresa.
* **Análisis de Factores:** Determinar qué variables (tipo de contrato, servicios contratados, método de pago, etc.) influyen más en la evasión.
* **Evitar el Sobreajuste (Overfitting):** Crear un modelo robusto y generalizable para nuevos datos.
* **Estrategias de Negocio:** Traducir los hallazgos técnicos en acciones de negocio concretas.

## 🛠️ Tecnologías y Herramientas Utilizadas
* **Lenguaje:** Python
* **Manipulación de Datos:** Pandas, NumPy
* **Visualización:** Matplotlib, Seaborn
* **Machine Learning:** Scikit-Learn (Regresión Logística, Random Forest)
* **Preprocesamiento:** StandardScaler, One-Hot Encoding (`get_dummies`), Label Encoding.

## ⚙️ Metodología y Pipeline de Datos
1. **Limpieza y Extracción:** Tratamiento de valores nulos, eliminación de columnas irrelevantes (`CustomerID`, `daily_charges`) y unificación de categorías.
2. **Análisis Exploratorio de Datos (EDA):** Evaluación de la proporción de cancelación, análisis de correlación numérica (Heatmap) y test de Chi-cuadrado para variables categóricas.
3. **Preprocesamiento:** Transformación de variables categóricas a numéricas y estandarización de características continuas. División del dataset en Entrenamiento (70%) y Prueba (30%).
4. **Modelado y Ajuste:** Entrenamiento de modelos de Regresión Logística y Random Forest. Se aplicó el hiperparámetro `class_weight='balanced'` para manejar el desbalance de clases y técnicas de poda (`max_depth`, `min_samples_leaf`) en el Random Forest para mitigar un caso severo de overfitting inicial.

<img width="919" height="519" alt="image" src="https://github.com/user-attachments/assets/b8bdc04c-86df-4c9e-a636-c34b8ba49a17" />


## 📊 Resultados del Modelo
Dado el contexto de negocio, la métrica principal a optimizar fue el **Recall (Sensibilidad)** en la clase minoritaria (Churn), ya que no detectar a un cliente que se va es más costoso que una falsa alarma.

Tras el ajuste de hiperparámetros, ambos modelos lograron capturar casi al **80% de los clientes en riesgo**:
* **Regresión Logística (Ajustada):** Recall: **79.8%** | F1-Score: 0.615
* **Random Forest (Ajustado):** Recall: **78.0%** | F1-Score: 0.621 *(Modelo seleccionado por su mejor equilibrio y robustez)*

## 💡 Principales Hallazgos de Negocio (Insights)
Al analizar la importancia de las características (Feature Importance) y los coeficientes logísticos, descubrimos que:

🔴 **Impulsores de Cancelación (Riesgo):**
* **Contratos mes a mes:** Los clientes sin compromiso a largo plazo tienen una barrera de salida mínima.
* **Internet de Fibra Óptica:** Muestra una alta tasa de cancelación, sugiriendo posibles problemas de calidad del servicio o precios poco competitivos.
* **Cheque Electrónico:** Los usuarios de este método de pago son inusualmente propensos al churn.

🟢 **Factores de Retención (Lealtad):**
* **Antigüedad (Tenure):** Superar los primeros meses es vital. A mayor antigüedad, el riesgo de churn se desploma.
* **Contratos a largo plazo (1 o 2 años):** Es el "blindaje" más fuerte contra la cancelación.
* **Servicios de Soporte (Tech Support / Online Security):** Actúan como anclas que mejoran la experiencia del usuario y evitan la frustración ante fallos técnicos.

## 🚀 Estrategias Propuestas para Telecom X
1. **Campaña de Migración:** Ofrecer descuentos agresivos en los primeros 3 meses a los clientes de "mes a mes" a cambio de firmar contratos de 1 año.
2. **Auditoría de Fibra Óptica:** Investigar la calidad, latencia y precio frente a la competencia de este servicio específico.
3. **Programa de Onboarding:** Implementar llamadas de cortesía y tutoriales técnicos durante los primeros 90 días del cliente para fomentar la maduración de la cuenta.

