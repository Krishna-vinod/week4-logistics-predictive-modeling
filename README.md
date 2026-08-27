# 🚚 Logistics Delivery Time Prediction

A machine learning-based system for predicting actual shipment delivery time using historical logistics data.

## 📌 Project Overview

This project predicts the actual number of days required to deliver a shipment based on shipment characteristics such as distance, weight, quantity, scheduled delivery time, shipping mode, region, product category, and priority.

Three regression models were evaluated:

- Linear Regression
- Random Forest Regressor
- Gradient Boosting Regressor

After comparison, **Linear Regression** was selected as the final model.

---

## 🎯 Objectives

- Predict actual delivery time for shipments.
- Identify factors influencing delivery duration.
- Compare multiple machine learning regression algorithms.
- Validate the selected model using 5-fold cross-validation.
- Analyze prediction errors and model generalization.
- Build a reusable prediction model for new shipments.

---

## 📊 Dataset

The dataset contains **2,001 shipment records**.

### Features

| Feature | Description |
|---|---|
| `Distance_km` | Shipment transportation distance |
| `Shipment_Weight_kg` | Shipment weight |
| `Order_Quantity` | Number of items ordered |
| `Scheduled_Days` | Planned delivery duration |
| `Shipping_Mode` | Shipping service type |
| `Region` | Destination region |
| `Product_Category` | Product category |
| `Priority` | Shipment priority |

### Target Variable

`Actual_Delivery_Days`

---

## ⚙️ Preprocessing

### Numerical Features

- Median imputation
- StandardScaler normalization

### Categorical Features

- Most-frequent-value imputation
- One-Hot Encoding
- Unknown categories handled safely

All preprocessing and prediction steps were combined into a Scikit-learn Pipeline.

---

## 🤖 Models Evaluated

| Model | MAE (days) | RMSE (days) | R² |
|---|---:|---:|---:|
| 🏆 **Linear Regression** | **0.982** | **1.204** | **0.365** |
| Gradient Boosting | 0.999 | 1.227 | 0.341 |
| Random Forest | 1.015 | 1.247 | 0.319 |

### 🏆 Best Model

**Linear Regression**

It achieved the lowest MAE and RMSE and the highest R² among the evaluated models.

---

## 🔄 5-Fold Cross-Validation

| Metric | Result |
|---|---:|
| Mean MAE | **0.977 ± 0.034 days** |
| Mean RMSE | **1.188 ± 0.045 days** |

The small standard deviations indicate consistent performance across the five folds.

---

## 📈 Final Test Performance

| Metric | Result |
|---|---:|
| Test MAE | **0.982 days** |
| Test RMSE | **1.204 days** |
| Test R² | **0.365** |
| Predictions within ±1 day | **62.59%** |
| Predictions within ±2 days | **90.77%** |
| Predictions within ±3 days | **99.00%** |

The model was evaluated on **401 unseen test samples**.

---

## 🧪 Baseline Comparison

A simple baseline model predicting the mean delivery time achieved:

| Metric | Baseline | Linear Regression |
|---|---:|---:|
| MAE | 1.226 | **0.982** |
| RMSE | 1.512 | **1.204** |
| R² | -0.001 | **0.365** |

Compared with the baseline, the proposed model achieved:

- **19.9% lower MAE**
- **20.4% lower RMSE**

---

## 🔍 Error Analysis

Residual analysis produced the following results:

- Mean residual: **0.031 days**
- Residual standard deviation: **1.206 days**
- Minimum residual: **−3.505 days**
- Maximum residual: **4.371 days**
- Correlation between actual and predicted values: **0.605**

### Prediction Accuracy

- **62.59%** of predictions were within ±1 day.
- **90.77%** were within ±2 days.
- **99.00%** were within ±3 days.

---

## 🔎 Feature Analysis

The strongest regression coefficients included:

| Feature | Coefficient |
|---|---:|
| `Scheduled_Days` | **+1.077** |
| `Shipping_Mode_Same Day` | +0.411 |
| `Shipping_Mode_Standard Class` | −0.368 |
| `Priority_Critical` | −0.110 |
| `Priority_Low` | +0.100 |

`Scheduled_Days` was the dominant predictor in the fitted model.

---

## 🔮 Example Prediction

For a new shipment with:

| Input | Value |
|---|---|
| Distance | 500 km |
| Weight | 10 kg |
| Quantity | 3 |
| Scheduled Days | 4 |
| Shipping Mode | First Class |
| Region | USCA |
| Product Category | Technology |
| Priority | High |

### 🚚 Predicted Delivery Time

**4.77 days**

---

## 🧠 Generalization Analysis

| Metric | Training | Test |
|---|---:|---:|
| MAE | 0.964 days | 0.982 days |
| RMSE | 1.169 days | 1.204 days |
| R² | 0.353 | 0.365 |

The small difference between training and test errors indicates no strong evidence of overfitting.

---

## 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Joblib
- Streamlit

---

## 📁 Project Structure

```text
week4-logistics-predictive-modeling/
│
├── README.md
├── app.py
├── requirements.txt
└── delivery_time_prediction_model.pkl

---

## 🚀 Future Scope
-Real-time GPS and shipment tracking
-Traffic and weather integration
-Carrier performance analysis
-Holiday and seasonal effects
-Real-time prediction API
-Interactive logistics dashboard
-Advanced ensemble and deep-learning models
-Automatic delay alerts

---

## 🏁 Conclusion

The project successfully developed a machine learning-based delivery-time prediction system.

Among the evaluated models, Linear Regression performed best, achieving an MAE of 0.982 days, RMSE of 1.204 days, and R² of 0.365.

The model demonstrated consistent cross-validation performance, with 90.77% of predictions within ±2 days of the actual delivery time.

Compared with a simple mean baseline, the proposed model reduced MAE by 19.9% and RMSE by 20.4%.

This demonstrates the potential of machine learning for practical delivery-time estimation and logistics decision support.
