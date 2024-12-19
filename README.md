# Housing Price Prediction

## Project Overview
This project aims to predict housing prices in Seattle (2014-2015) using machine learning techniques. The main objectives are:

- Accurately forecast housing prices under and above $1 million.
- Provide data-driven insights to assist real estate professionals and potential buyers.
- Identify key factors influencing housing prices and optimize predictive models.

## Dataset Information
- **Source**: Kaggle dataset of Seattle real estate transactions.
- **Size**: 21,613 rows and 21 columns.
- **Features**: Includes bedrooms, bathrooms, living space size, lot size, transaction price, and more.

## Methodology
### 1. Exploratory Data Analysis (EDA)
- Target variable (housing prices) is right-skewed, with most values below $1 million.
- Outliers were observed in higher price ranges.

### 2. Feature Engineering
- Created new features:
  - `basement`: Binary variable indicating if a house has a basement.
  - `renovated`: Binary variable indicating if a house has been renovated.
  - `avg_price_by_zipcode`: Average housing price by postal code.
- Logarithmic transformations applied to reduce skewness.
- Clustering applied to geographic coordinates.

### 3. Feature Selection
- Selected features based on importance (>0.05) using a Random Forest Classifier:
  - `area`, `m2_living`, `grade`, `avg_price_by_zipcode`, `m2_above`, `bathrooms`, and `m2_living15`.

### 4. Predictive Modeling
#### Classificatory Model (Price Threshold: $1 Million)
- **Class 0**: Houses priced under $1 million.
- **Class 1**: Houses priced at or above $1 million.
- Best model: **XGBoost Classifier** (without balancing techniques).

#### Regression Model for Class 0
- Models trained: Ridge, Lasso, Random Forest, XGBoost, Support Vector Regression.
- Best model: **XGBoost**, with lowest RMSE and highest R².

#### Classification Model for Class 1
- Categorized luxury prices into three groups due to data imbalance.
- Best model: **XGBoost Classifier**, achieving moderate performance (Accuracy: 65.55%).

## Results
- **Class 0**:
  - Best model: XGBoost.
  - Metrics: RMSE = 71,360, MAE = 52,190, R² = 0.86.
- **Class 1**:
  - Best model: XGBoost.
  - Accuracy: 65.55%, F1-macro: 0.65.

## Next Steps
1. Validate models on external datasets to ensure generalization.
2. Explore additional feature engineering opportunities.
3. Deploy models for real-time predictions.
4. Monitor and update models with new data regularly.

## Acknowledgements
This project utilized data from Kaggle and machine learning techniques including Random Forest, XGBoost, and Support Vector Machines. Special thanks to all contributors for their valuable insights and support.
