# store_sales_forecast_sarimax
Time series analysis and forecast for Kaggle Playground Code Challenge: https://www.kaggle.com/competitions/demand-forecasting-kernels-only/

### Brief
- This competition is provided as a way to explore different time series techniques on a relatively simple and clean dataset.
- You are given 5 years of store-item sales data, and asked to predict 3 months of sales for 50 different items at 10 different stores.
- What's the best way to deal with seasonality? Should stores be modeled separately, or can you pool them together? Does deep learning work better than ARIMA? Can either beat xgboost?

(There are 10 stores, and 50 items on sale.)

### Notebooks Summary
- `storesales_modelselection.ipynb` - EDA, feature engineering, model selection
- `storesales_prediction.ipynb`     - streamlined code for batch generating individual models and predictions for each item-store set

**Feature Engineering for exogenous features**
  - US holidays
  - seasonal_decompose(period=365).seasonal (as SARIMAX was trained on period=7)

**Model Selection**
  - using auto ARIMA and further param tuning to hone in on the model with best balance of score/computation required.
  - selected SARIMAX(3,1,1)(1,1,1,7)
  
**Batch Model Training & Prediction**
  - second notebook generates predictions into .csv for Kaggle submission.
  - SMAPE score of about 9.8 on test data, and 15.76531 on out-of-sample data.
