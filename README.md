#  🏠 Predicción y Detección de Propiedades Subvaluadas en Cataluña

Este proyecto aplica Machine Learning para estimar el valor de mercado de propiedades en Cataluña y detectar aquellas que están significativamente por debajo de su valor estimado, generando un ranking de oportunidades de inversión.

## 📍 Contexto

El análisis se realiza sobre datos inmobiliarios de Cataluña, con variables como:

Ubicación (nom_comar, municipality, coordenadas geográficas)

Características físicas (superficie, habitaciones, baños, ascensor, planta)

Clasificación por tamaño (cat_size) y altura (floor_grouped)

Variables derivadas y de interacción

Distancia geográfica a Plaça de Catalunya

## 🔍 Metodología

Preprocesamiento de datos

Limpieza y tratamiento de outliers

Codificación ordinal para categorías con jerarquía

Frequency Encoding para municipality

Feature Engineering

Ratios: rooms_per_100m, bath_per_room

Interacciones: hasLift × floor

Distancia a punto de referencia central

Modelado

Comparativa: RidgeCV (regresión regularizada) vs. Gradient Boosting Regressor

Validación cruzada estratificada por comarca

Criterio de subvaloración

Precio real ≥ 10% inferior al estimado por el modelo

Ranking ponderado por % de subvaloración y z-score del residuo

## 📊 Resultados y archivos

Se generan automáticamente en ..\data:

propiedades_subvaluadas.xlsx / .csv → listado completo con métricas y enlace directo a Idealista

top3_por_comarca.xlsx / .csv → mejores 3 oportunidades por comarca

Cada registro incluye:

Código de propiedad (propertyCode)

Precio real y estimado

% de subvaloración

Z-score de residuo

Puntaje de prioridad

Enlace clicable a la oferta en Idealista

Ejemplo de enlace:
https://www.idealista.com/inmueble/12345678/

🗺 Visualizaciones recomendadas

Mapa → color según % de subvaloración, tamaño según precio

Top 3 por comarca → gráfico de barras horizontales

Tabla interactiva → búsqueda y filtrado en Power BI / Tableau

## ️ Nota

El análisis es predictivo y no sustituye la verificación manual del inmueble. Antes de invertir, evaluar:

Estado físico

Ubicación exacta y entorno

Licencias y documentación legal