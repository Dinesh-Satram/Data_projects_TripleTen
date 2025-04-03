# Used Car Price Prediction with Machine Learning

## Project Overview
Rusty Bargain is developing an app that allows users to quickly estimate the market value of their used car based on historical data. The goal of this project is to build a machine learning model that can predict the price of a used car accurately, while also ensuring fast training and prediction times. The models used for this prediction will be compared for their speed and quality, focusing on RMSE (Root Mean Squared Error) as the primary evaluation metric.

## Data Description
The dataset is stored in `car_data.csv`, and contains the following features:

- **DateCrawled**: Date when the car ad was crawled.
- **VehicleType**: Type of the vehicle body.
- **RegistrationYear**: The year the car was registered.
- **Gearbox**: Gearbox type (manual/auto).
- **Power**: Power of the vehicle in horsepower.
- **Model**: Vehicle model.
- **Mileage**: Mileage of the car in kilometers.
- **RegistrationMonth**: Month of registration.
- **FuelType**: Type of fuel used.
- **Brand**: Car brand.
- **NotRepaired**: Whether the car has been repaired.
- **DateCreated**: Date the profile was created.
- **NumberOfPictures**: Number of pictures of the car.
- **PostalCode**: Postal code of the car’s owner.
- **LastSeen**: Last seen date of the car ad.
- **Target (Price)**: Price of the car (in Euro).

The target variable is **Price** (price in Euro).

## Steps in the Project

### 1. **Data Preparation**
- Load and inspect the dataset to understand its structure.
- Clean the data by handling duplicates and irrelevant columns.
- Deal with missing values by filling categorical features with "unknown".
- Filter out unrealistic values for features like **RegistrationYear**, **Power**, and **Price**.
- Apply **One-Hot Encoding** for categorical features, and retain categorical data for models like **LightGBM** and **CatBoost**.

### 2. **Feature Engineering**
- Prepare datasets for models requiring One-Hot Encoding (OHE) and those that support categorical features (LightGBM & CatBoost).
- Scale numerical features for models like **Linear Regression** and **Random Forest**.

### 3. **Model Training**
The following models were trained and compared:
- **Linear Regression** (used for sanity check)
- **Decision Tree Regressor**
- **Random Forest Regressor**
- **LightGBM Regressor** (with hyperparameter tuning)
- **XGBoost Regressor** (with hyperparameter tuning)

### 4. **Model Evaluation**
Models were evaluated based on:
- **RMSE (Root Mean Squared Error)** to assess prediction quality.
- **Training time** to evaluate model efficiency.
- **Prediction time** to evaluate how fast the model predicts values.

### 5. **Hyperparameter Tuning**
- **XGBoost** was tuned using **RandomizedSearchCV** to optimize the hyperparameters, such as `n_estimators`, `learning_rate`, `max_depth`, etc.

### 6. **Model Deployment**
The **LightGBM model** was saved using `joblib` and tested with a sample input to verify its prediction capability in real-time.

### 7. **Final Analysis**
- **LightGBM** emerged as the best-performing model with the lowest RMSE and fast training time.
- **Random Forest** and **XGBoost** also performed well but required more training time and were slower.
- **Decision Tree** and **Linear Regression** were less effective.

## Key Findings

| Model                 | RMSE      | Training Time (s) | Prediction Time (s) |
|-----------------------|-----------|-------------------|---------------------|
| Linear Regression      | 2586.64   | 8.68              | 0.1027              |
| Decision Tree          | 1992.44   | 2.64              | 0.0537              |
| Random Forest          | 1677.16   | 201.83            | 1.1177              |
| LightGBM               | 1630.34   | 2.71              | 0.5006              |
| XGBoost (Tuned)        | 1754.45   | 176.61            | 0.5680              |

**LightGBM** showed the best performance in terms of both **RMSE** and **training speed**, while **Random Forest** also performed well with a slightly higher RMSE but longer training time. **XGBoost** performed slower and had a slightly higher RMSE compared to LightGBM and Random Forest.

## Conclusion

- **LightGBM** was found to be the best model for predicting used car prices in terms of both accuracy (low RMSE) and speed (fast training and prediction).
- **Random Forest** also showed strong performance but required significantly more training time.
- **XGBoost** performed slower than expected and showed a higher RMSE, suggesting that further tuning may be needed.
- The model has been successfully deployed for real-time predictions, and it is ready for use in the Rusty Bargain app.

## How to Run the Project

### Prerequisites:
Install the required libraries:
```bash
pip install pandas numpy scikit-learn lightgbm xgboost catboost matplotlib joblib
