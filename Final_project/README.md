# Customer Churn Prediction for Interconnect: A Machine Learning Approach

## Project Overview

Customer churn is a major concern for telecom operators, as retaining existing customers is often more cost-effective than acquiring new ones. This project focuses on building a machine learning model to predict customer churn for the telecom operator Interconnect. By identifying customers likely to churn, the company can implement targeted retention strategies, such as offering promotional codes or special plan options.

The dataset used for this project contains customer information, including personal data, contract details, internet services, and phone services. The target variable is whether a customer has churned, indicated by the "EndDate" column, which is used to predict the likelihood of customer churn.

## Data Description

The dataset consists of four CSV files containing different aspects of customer information:

- **contract.csv**: Contains contract details like the contract type, payment method, and monthly charges.
- **personal.csv**: Includes personal information such as gender, senior citizen status, partner, and dependents.
- **internet.csv**: Provides details about internet services, including security features and streaming options.
- **phone.csv**: Contains phone service information, such as whether the customer has multiple lines.

The target variable is the 'EndDate' column, where a value of 'No' indicates an active customer.

## Project Steps

### 1. **Data Loading and Inspection**
The data from four datasets (contract, personal, internet, phone) was loaded and inspected for structure, missing values, and initial insights.

### 2. **Data Preprocessing and Cleaning**
- Missing values were handled appropriately, filling missing data for columns such as 'TotalCharges' and 'EndDate'.
- The 'Churn' column was created to indicate whether a customer has churned.
- The datasets were merged into a single DataFrame using the `customerID` column.
- One-hot encoding was applied to categorical features such as contract type, payment method, and internet service type.

### 3. **Exploratory Data Analysis (EDA)**
- **Churn Distribution**: The churn distribution was highly imbalanced, with more active customers than churned ones.
- **Contract Type and Churn**: It was observed that month-to-month contracts had the highest churn rate, while longer-term contracts had lower churn rates.
- **Monthly and Total Charges**: Higher monthly and total charges were correlated with a higher likelihood of churn.
- **Contract Duration**: A strong inverse relationship between contract duration and churn was observed.

### 4. **Feature Engineering**
- **Contract Duration**: A new feature, 'contract_duration', was created to represent the number of months a customer has been with the company.
- Categorical variables were encoded using one-hot encoding.

### 5. **Model Building and Training**
Several machine learning models were built and evaluated, including:
- **Logistic Regression**: A baseline model with an AUC-ROC score of 0.8291 and a testing accuracy of 0.7331.
- **Decision Tree Classifier**: A moderately performing model with an AUC-ROC score of 0.6561 and a testing accuracy of 0.7296.
- **Random Forest Classifier**: A strong performer with an AUC-ROC score of 0.8224 and a testing accuracy of 0.7885.
- **XGBoost Classifier**: A reasonable performer with an AUC-ROC score of 0.8152 and a testing accuracy of 0.7544.

### 6. **Hyperparameter Tuning**
- **Random Forest**: A tuned Random Forest model achieved an improved AUC-ROC score of 0.8354.
- **XGBoost**: A tuned XGBoost model achieved an AUC-ROC score of 0.8255.

### 7. **Model Evaluation and Comparison**
- The tuned Random Forest model showed the best performance, with improved recall for churned customers (Class 1), achieving an AUC-ROC score of 0.8354.
- Feature importance analysis revealed that the most significant features influencing churn are **total charges**, **monthly charges**, **contract type**, and **internet service type**.

## Model Performance

| Model               | Accuracy (Test) | AUC-ROC Score (Test) | Key Observations                                                                 |
|---------------------|-----------------|----------------------|----------------------------------------------------------------------------------|
| Logistic Regression | 0.7331          | 0.8291               | High recall for churned customers, but low precision.                           |
| Decision Tree       | 0.7296          | 0.6561               | Moderate performance, struggling to identify churned customers effectively.     |
| Random Forest       | 0.7885          | 0.8224               | Good performance on Class 0, but struggles with Class 1 (churned customers).    |
| XGBoost             | 0.7544          | 0.8152               | Reasonable performance, struggles with churned customers but performs well overall.|
| Tuned Random Forest | 0.7764          | 0.8354               | Best overall performance, with better recall for churned customers.             |
| Tuned XGBoost       | 0.7658          | 0.8255               | Slightly underperforms compared to tuned Random Forest.                         |

## Key Findings

- **Contract Type**: Month-to-month contracts are more likely to churn, whereas longer-term contracts (One-Year and Two-Year) show lower churn rates.
- **Charges**: Higher **monthly charges** and **total charges** are strongly associated with churn.
- **Senior Citizens**: Senior citizens show a slightly higher likelihood of churn.
- **Feature Importance**: The most important features for churn prediction are **total charges**, **monthly charges**, **contract type**, and **internet service type**.

## Conclusion

The project successfully predicted customer churn for Interconnect using various machine learning models. The tuned Random Forest model performed the best, with the highest AUC-ROC score of 0.8354. The feature importance analysis revealed that **total charges**, **monthly charges**, and **contract type** were the most influential factors contributing to churn.

This model can be deployed to predict customer churn in real-time, enabling the marketing team to offer targeted promotions to retain valuable customers.

## Future Improvements

- **Handling Imbalance**: The class imbalance in churn distribution could be addressed through techniques like oversampling, undersampling, or adjusting class weights.
- **Additional Features**: Including more features such as customer service interactions or usage data might improve the model's predictive power.
- **Model Performance**: Further tuning and experimenting with other models (e.g., neural networks) could yield better results.

## How to Run the Project

### Prerequisites:
Install the required libraries:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost
