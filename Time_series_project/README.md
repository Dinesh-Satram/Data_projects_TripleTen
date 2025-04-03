# Taxi Demand Prediction: Forecasting Hourly Orders for Sweet Lift Taxi

## Project Overview
Sweet Lift Taxi is aiming to improve its service by predicting the number of taxi orders for the next hour at airports. This will help the company attract more drivers during peak hours. The goal of this project is to build a machine learning model to predict taxi demand based on historical data, with the performance target of achieving an RMSE (Root Mean Squared Error) of ≤ 48 on the test set.

## Data Description
The dataset is stored in `taxi.csv` and contains the following columns:
- **datetime**: The timestamp of the taxi order.
- **num_orders**: The number of taxi orders at that time.

### File Structure:
- **taxi.csv**: The dataset containing historical data on taxi orders.

## Project Steps

### 1. **Data Loading and Inspection**
- The data is loaded from the `taxi.csv` file.
- The `datetime` column is converted to the `datetime64` format for proper time series analysis.
- The `num_orders` column is checked for its correctness (integer type).

### 2. **Data Preparation**
- Duplicate rows are checked and removed (none found in the dataset).
- The `datetime` column is set as the index for proper time series analysis.
- The dataset is sorted chronologically to ensure accurate modeling.

### 3. **Resampling**
- The data is resampled to an hourly frequency by summing up the `num_orders` for each hour.

### 4. **Feature Engineering**
- Time-based features are created from the `datetime` index:
  - **hour**: Hour of the day.
  - **day_of_week**: Day of the week.
  - **month**: Month of the year.

### 5. **Data Splitting**
- The dataset is split into a training set (90%) and a test set (10%).

### 6. **Model Training**
- **Baseline Model (Linear Regression)**: This model is trained on the time-based features to serve as a baseline check.
- **Advanced Model (Random Forest Regressor)**: The Random Forest model is trained on the same features to improve upon the baseline performance.

### 7. **Model Evaluation**
- **RMSE**: The Root Mean Squared Error is calculated for each model to evaluate its prediction accuracy.
- **Final Model**: The Random Forest model achieves an RMSE of 46.97, meeting the target RMSE ≤ 48.

### 8. **Model Visualization**
- A plot is generated comparing the actual and predicted taxi orders to visually evaluate the model's performance.

## Key Findings

| Model                   | RMSE    | Training Time (s) | Prediction Time (s) |
|-------------------------|---------|-------------------|---------------------|
| Linear Regression        | 66.53   | -                 | -                   |
| Random Forest            | 46.97   | 201.83            | 1.1177              |

- **Linear Regression** had an RMSE of 66.53, which exceeded the target RMSE, and did not capture the non-linear patterns in the data effectively.
- **Random Forest** significantly outperformed Linear Regression with an RMSE of 46.97, successfully capturing non-linear patterns and seasonal trends in taxi demand.

## Conclusion

The Random Forest model achieved an RMSE of 46.97, successfully meeting the project requirement of an RMSE ≤ 48. This model is suitable for forecasting taxi demand and can help Sweet Lift Taxi optimize driver allocation during peak hours. The model performs well in capturing hourly and daily demand patterns but may need further tuning for extreme peak hours.

### Future Recommendations:
- Additional feature engineering could be performed to improve prediction accuracy for extreme demand spikes.
- Other models like **XGBoost** and **LightGBM** can be tested for further optimization.

## How to Run the Project

### Prerequisites:
Install the required libraries:
```bash
pip install pandas numpy matplotlib scikit-learn statsmodels
