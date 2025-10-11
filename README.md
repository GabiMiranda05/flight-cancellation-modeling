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
