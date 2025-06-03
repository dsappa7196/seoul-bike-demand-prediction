# seoul-bike-demand-prediction

# 🚲 Seoul Bike Sharing Demand Prediction

📦 **Project Type**: Time-Series Regression | Machine Learning for Urban Planning  
🎓 **Course**: DS 861 – Predictive Modeling | San Francisco State University  
👩‍💻 **Author**: Padmasree Sappa  
📁 Tools: Python, Pandas, Scikit-learn, Matplotlib, Seaborn, Gradient Boosting

---

## 🧠 Project Overview

With Seoul’s smart city vision gaining momentum, bicycle-sharing is an integral part of sustainable urban mobility. However, unpredictable rental demand creates major challenges in inventory management and resource planning. 

This project addresses that challenge by building a machine learning pipeline to accurately predict **hourly bike rental counts** using historical, weather, and calendar data. The solution integrates full-cycle modeling — from EDA and outlier handling to regression comparisons, cross-validation, and hyperparameter tuning — structured using the CRISP-DM methodology.

> 🎯 Final model: **Gradient Boosting Regressor with R² = 0.92**, validated with learning curves and residual analysis.

---

## 📊 Dataset

- 📁 Source: UCI Machine Learning Repository  
- 📈 Size: 8,760 hourly records × 14 columns (1 year)  
- 🧾 Target: `Rented Bike Count`

### Key Features:
- Temporal: `Hour`, `Day`, `Month`, `Weekday`, `Is_Weekend`
- Weather: `Temperature`, `Humidity`, `Wind Speed`, `Visibility`, `Solar Radiation`, `Rainfall`, `Snowfall`
- Calendar: `Holiday`, `Functioning Day`, `Season`

---

## 📐 CRISP-DM Pipeline Summary

### 1. **Business Understanding**
- Problem: Inconsistent rental behavior leads to over/under-supply
- Goal: Predict hourly demand for operational optimization

### 2. **Data Understanding & Cleaning**
- Validated 8,760 rows for consistency
- Removed outliers with IQR method but **decided to retain them** to preserve rare but impactful events (rainfall/snowfall)
- Converted categorical variables and engineered temporal features (`Day_Name`, `Is_Weekend`, `Season`)

### 3. **EDA Highlights**
- Rentals peak **8AM & 6PM** on weekdays (commuter hours)
- Rentals decline sharply in **winter** and on **holidays**
- Weekday demand is structured and higher than weekend leisure patterns

### 4. **Modeling**
- Split: 64% train / 16% validation / 20% test (avoiding data leakage)
- Scaling: `StandardScaler` applied post split
- Dummy Regressor baseline established

### 5. **Algorithms Compared**
- 🔹 Linear Models: Ridge, Lasso, ElasticNet (R² ≈ 0.54)
- 🌲 Tree Models: Decision Tree, Random Forest, Gradient Boosting
- 🤖 Others: KNN, SVR, MLP

✅ **Best Model**: Gradient Boosting Regressor
- R² = 0.92
- MAE ≈ 109, RMSE ≈ 173

### 6. **Cross-Validation & Tuning**
- Used `GridSearchCV` on top models
- Gradient Boosting tuned on `n_estimators`, `max_depth`, `learning_rate`

### 7. **Model Evaluation & Diagnostics**
- Learning Curves: Low variance, low bias
- Residuals: Symmetric, centered → minimal systemic error
- Feature Importance:
  - `Hour`, `Temperature`, and `Dew Point` drive predictions
  - Rainfall/Snowfall had low predictive power

---

## 🗂 Files Included

| File Name                      | Description                                      |
|-------------------------------|--------------------------------------------------|
| [SeoulBike_Model.ipynb](https://github.com/dsappa7196/seoul-bike-demand-prediction/blob/main/DataMining_SeoulBikeSharingDemand_Project.ipynb) | Full Python notebook with model pipeline         |
| [SeoulBike_Report.pdf](https://github.com/dsappa7196/seoul-bike-demand-prediction/blob/main/DS861_SeoulBikeSharingDemandPrediction_Sappa.pdf)   | Final detailed report                             |
| [SeoulBike_Deck.pptx](https://github.com/dsappa7196/seoul-bike-demand-prediction/blob/main/DS861_SeoulBikeSharingDemandPrediction_Sappa.pptx)     | Slide deck for presentation                      |
| [SeoulBike_Data.xlsx]([./SeoulBike_Data.csv](https://github.com/dsappa7196/seoul-bike-demand-prediction/blob/main/SeoulBikeData.xlsx))       | Cleaned dataset                                  |

---

## ✅ Business Impact

This model enables:
- 🚲 Fleet planning and rebalancing across time slots
- 👷‍♂️ Staff scheduling based on demand windows
- 🛠 Predictive maintenance with demand drops
- 📊 Data-driven decisions for promotions & campaigns

---

## 🔮 Future Scope
- Integrate **live weather APIs** for real-time predictions
- Transition model to **time-series LSTM**
- Deploy as a web app using Streamlit
- Add geospatial data for station-level insights

---

> _“Bike rentals are human behavior in motion — and now, with data, they’re predictable.”_
