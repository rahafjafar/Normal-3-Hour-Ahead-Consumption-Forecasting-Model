
# 3-Hour Water Consumption Forecasting Model

## Overview
This project implements a Machine Learning model to predict total household water consumption over the next three hours (t+1, t+2, t+3).

The model uses historical water consumption data and time-based features to identify household consumption patterns and generate short-term forecasts.

## Methodology

### 1. Data Preparation
- Loaded and sorted the cleaned Jordanian water consumption dataset.
- Filtered the data to include only normal consumption periods.
- Constructed the target variable using the total consumption of the next three hours.
- Prevented data leakage by ensuring future readings are used only for target construction, not as model inputs.

### 2. Feature Engineering
Three main feature groups were developed:
- **Time Features:** Cyclic encoding of hours and days.
- **Weekly Refill Cycle Features:** Features representing hours since refill, hours until refill, and refill position, based on a 168-hour weekly cycle.
- **Historical Features:** Lag values and rolling statistical features to capture previous consumption patterns.

### 3. Model Training
Seven regression algorithms were compared:
- Linear Regression
- Ridge
- Lasso
- ElasticNet
- Random Forest
- Extra Trees
- HistGradientBoostingRegressor

HistGradientBoostingRegressor was selected and optimized using a three-stage tuning process:
1. L2 Regularization Search
2. Manual Random Search
3. Quantum-behaved Particle Swarm Optimization (QPSO)

### 4. Evaluation
The dataset was split chronologically:
- 60% Training
- 20% Validation
- 20% Testing

The final model was evaluated using MAE, RMSE, SMAPE, and R².

## Final Results

| Metric | Test Result |
|---|---:|
| MAE | 12.80 |
| RMSE | 17.56 |
| SMAPE | 12.35% |
| R² | 0.9102 |

**Selected Model:** QPSO_HGB (HistGradientBoostingRegressor)

## Saved Artifacts
- `optimized_3h_normal_consumption_forecasting_model.pkl`
- `optimized_3h_forecasting_validation_results.csv`
- `optimized_3h_forecasting_feature_importance.csv`
- `optimized_3h_forecasting_final_metrics.csv`

## Technologies
Python, Pandas, NumPy, Scikit-learn, Matplotlib, Joblib.

## Purpose
The model provides short-term consumption forecasts that can support water management, consumption monitoring, and downstream recommendation and anomaly detection modules.
