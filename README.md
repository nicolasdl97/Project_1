# 🏠 Predicting and Detecting Undervalued Properties in Catalonia  

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue)](https://www.python.org/)  
[![scikit-learn](https://img.shields.io/badge/scikit--learn-ML%20Model-orange)](https://scikit-learn.org/stable/)  
[![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-lightgrey)](https://pandas.pydata.org/)  

This project applies **Machine Learning** to estimate the market value of properties in **Catalonia** and detect those **significantly below their estimated value**, producing a ranking of potential investment opportunities.  

---

## 📍 Context  
The analysis is based on Catalonia real estate listings, including:  
- Location (`nom_comar`, `municipality`, geographic coordinates)  
- Physical characteristics (size, rooms, bathrooms, lift, floor level)  
- Size category (`cat_size`) and floor grouping (`floor_grouped`)  
- Engineered and interaction features  
- Distance to a central reference point (**Plaça de Catalunya**)  

---

## 🔍 Methodology  
1. **Data Preprocessing**  
   - Data cleaning and outlier handling  
   - Ordinal encoding for hierarchical categories  
   - *Frequency Encoding* for `municipality`  
2. **Feature Engineering**  
   - Ratios: `rooms_per_100m`, `bath_per_room`  
   - Interactions: `hasLift × floor`  
   - Distance to a central reference point  
3. **Modeling**  
   - Comparison: **RidgeCV** (regularized regression) vs. **Gradient Boosting Regressor**  
   - Stratified cross-validation by `nom_comar`  
4. **Undervaluation Criteria**  
   - A property is considered **undervalued** if its actual price is **≥10% lower** than the model’s estimate  
   - Ranking weighted by % undervaluation and residual *z-score*  

---

## 📊 Results & Outputs  
Files are generated in `..\data`:  
- **`propiedades_subvaluadas.xlsx / .csv`** → full list with metrics and direct Idealista link  
- **`top3_por_comarca.xlsx / .csv`** → top 3 opportunities per comarca  

Each record includes:  
- Property code (`propertyCode`)  
- Actual and estimated price  
- % undervaluation  
- Residual *z-score*  
- Priority score  
- **Clickable link** to the Idealista listing  

**Example link:**  
`https://www.idealista.com/inmueble/12345678/`

---

## 🗺 Recommended Visualizations  
- **Map** → color by % undervaluation, size by price  
- **Top 3 per comarca** → horizontal bar chart  
- **Interactive table** → search and filter in Power BI / Tableau  

---

## ⚠️ Disclaimer  
This analysis is predictive and statistical. Results should be manually verified (property condition, exact location, legal documentation) before making any investment decision.  
