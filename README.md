## Predicción de Cancelaciones de Vuelos  

Este proyecto tiene como objetivo predecir la cancelación de vuelos comerciales mediante algoritmos de clasificación de Machine Learning.  
Para ello, se realiza un análisis exploratorio de datasets, que contiene información operativa y geográfica de vuelos, aeropuertos y aerolíneas, junto con variables temporales y de estado.  
En etapas posteriores se prevé incorporar fuentes externas, como datos meteorológicos y niveles de congestión del sistema aéreo, para mejorar la precisión del modelo.

---

### Descripción de variables

| Columna | Descripción |
|----------|--------------|
| **YEAR** | Año del vuelo programado. |
| **MONTH** | Mes del vuelo (valor numérico de 1 a 12). |
| **DAY** | Día del mes en que el vuelo estaba programado. |
| **DAY_OF_WEEK** | Día de la semana (1 = lunes, 7 = domingo). |
| **ORIGIN_AIRPORT** | Código del aeropuerto de origen (IATA). |
| **DESTINATION_AIRPORT** | Código del aeropuerto de destino (IATA). |
| **SCHEDULED_DEPARTURE** | Hora programada de salida del vuelo (en formato HHMM). |
| **SCHEDULED_TIME** | Duración programada del vuelo, en minutos. |
| **DISTANCE** | Distancia entre el aeropuerto de origen y destino, en millas. |
| **SCHEDULED_ARRIVAL** | Hora programada de llegada del vuelo (en formato HHMM). |
| **DIVERTED** | Indica si el vuelo fue desviado (1 = sí, 0 = no). |
| **CANCELLED** | Indica si el vuelo fue cancelado (1 = cancelado, 0 = no cancelado). |
| **CANCELLATION_REASON** | Motivo de la cancelación (ej. Weather, Airline, National Air System, Security). |
| **ORIGIN_STATE** | Estado o región asociada al aeropuerto de origen. |
| **ORIGIN_LATITUDE** | Latitud geográfica del aeropuerto de origen. |
| **ORIGIN_LONGITUDE** | Longitud geográfica del aeropuerto de origen. |
| **DESTINATION_STATE** | Estado o región asociada al aeropuerto de destino. |
| **DESTINATION_LATITUDE** | Latitud geográfica del aeropuerto de destino. |
| **DESTINATION_LONGITUDE** | Longitud geográfica del aeropuerto de destino. |
| **AIRLINE_NAME** | Nombre completo de la aerolínea operadora del vuelo. |

---

## Hipótesis de trabajo  

1. La probabilidad de cancelación varía según el momento del día, siendo mayor en determinadas franjas horarias.  
2. Existen diferencias en la tasa de cancelaciones a lo largo de la semana.  
3. Las aerolíneas presentan distintos niveles de cancelaciones.  

---

## Objetivo del modelo  

El objetivo del modelo es **predecir si un vuelo comercial será cancelado** (variable binaria), utilizando información disponible antes de la salida del vuelo.  
Dado el fuerte desbalance entre vuelos cancelados y no cancelados, el análisis se enfoca en **detectar la mayor cantidad posible de cancelaciones**, manteniendo un compromiso razonable con los falsos positivos.

---

## Preparación y procesamiento de los datos  

Antes del entrenamiento de los modelos, se realizaron las siguientes etapas de preprocesamiento:

- Limpieza de valores faltantes y registros inconsistentes.  
- Codificación de variables categóricas (aeropuertos, aerolíneas y estados).  
- Transformación de variables temporales (hora programada, día de la semana).
- División del dataset en conjuntos de entrenamiento y prueba, preservando la proporción de clases.  

---

## Modelos de Machine Learning  

Se entrenaron y evaluaron los siguientes modelos de clasificación:

- **Decision Tree Classifier**  
  Utilizado como modelo base debido a su interpretabilidad y bajo costo computacional.  

- **Random Forest Classifier**  
  Seleccionado como modelo principal por su mejor capacidad de generalización, mayor estabilidad frente al desbalance de clases y mejor desempeño en la detección de vuelos cancelados.  

> No se incluyeron modelos basados en distancia, como K-Nearest Neighbors (KNN), debido a su **alto costo computacional y baja escalabilidad** en conjuntos de datos de gran tamaño.

---

## Métricas de evaluación  

Debido al fuerte desbalance entre las clases, **la exactitud (accuracy) no se utilizó como métrica principal**.  
El desempeño de los modelos fue evaluado utilizando:

- **Recall de la clase CANCELLED (1)**  
- **Precision de la clase CANCELLED (1)**  
- **F1-score**  
- **Promedio macro de las métricas**  

El análisis se centró en **maximizar el recall de cancelaciones**, con el objetivo de reducir la cantidad de vuelos cancelados no detectados por el modelo.

---

## Resultados principales  

El modelo **Random Forest** presentó un desempeño superior al árbol de decisión individual, logrando:

- Un recall de cancelaciones cercano al **75–78%**.  
- Resultados consistentes entre los conjuntos de entrenamiento y prueba.  
- Un mejor equilibrio entre recall y precision para la clase minoritaria.  

Estos resultados indican que el modelo es capaz de identificar la mayoría de las cancelaciones, aunque aún presenta una proporción elevada de falsos positivos.

---

## Limitaciones y trabajo futuro  

- El modelo no incorpora información meteorológica, uno de los principales factores de cancelación de vuelos.  
- No se consideran variables operativas en tiempo real, como congestión aérea o retrasos acumulados.  
- En trabajos futuros se prevé:  
  - Incorporar datos meteorológicos.  
  - Evaluar modelos de Gradient Boosting (XGBoost, LightGBM, CatBoost).  
  
