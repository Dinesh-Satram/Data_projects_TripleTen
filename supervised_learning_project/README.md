# Predicting Customer Churn at Beta Bank

## Project Overview

In this project, we focus on predicting customer churn for Beta Bank. The bank has noticed that retaining existing customers is more cost-effective than acquiring new ones. Therefore, by predicting which customers are likely to leave, Beta Bank can implement targeted retention strategies. The goal is to build a machine learning model that predicts customer churn with an F1 score of at least 0.59. Additionally, the model will be evaluated using other metrics like AUC-ROC.

## Project Structure


- **README.md**: This file, which provides an overview of the project, setup instructions, and results.
- **churn_prediction.ipynb**: Jupyter notebook containing code for data exploration, model training, evaluation, and testing.
- **datasets/Churn.csv**: The dataset with customer behavior and churn information.
- **models/random_forest_model.pkl**: A saved RandomForest model for deployment (optional).

## Project Description

### 1. **Data Preparation and Exploration**
The dataset contains customer information such as credit score, age, account balance, number of products, and whether the customer has exited (churned). The key target variable is `Exited`, which indicates if a customer has left the bank (1) or stayed (0).

#### Key Features:
- **CreditScore**: Credit score of the customer.
- **Geography**: The country of residence.
- **Gender**: The gender of the customer.
- **Age**: Age of the customer.
- **Tenure**: The duration the customer has been with the bank (in years).
- **Balance**: The account balance.
- **NumOfProducts**: Number of banking products the customer has.
- **HasCrCard**: Whether the customer has a credit card.
- **IsActiveMember**: Whether the customer is an active member of the bank.
- **EstimatedSalary**: Estimated salary of the customer.

### 2. **Data Preprocessing**
- Missing values in the `Tenure` column were handled by replacing them with the median value.
- Irrelevant columns such as `RowNumber`, `CustomerId`, and `Surname` were dropped.
- Categorical features such as `Geography` and `Gender` were encoded using one-hot encoding.

### 3. **Class Imbalance**
The target variable `Exited` showed a significant imbalance, with 7,963 non-churned customers and only 2,037 churned customers. This imbalance could lead to biased models. We handled this imbalance using:
- **Class Weighting**: Applied to the RandomForestClassifier.
- **Upsampling**: Increased the minority class to balance the dataset.
- **Downsampling**: Reduced the majority class to balance the dataset.

### 4. **Model Training and Evaluation**
The model was trained using a **RandomForestClassifier** with class weighting, followed by upsampling and downsampling techniques to address the imbalance. We also performed hyperparameter tuning to optimize the model's performance.

#### Key Metrics:
- **F1 Score**: Measures the balance between precision and recall.
- **AUC-ROC**: Evaluates the ability of the model to distinguish between churned and non-churned customers.

### 5. **Final Model Performance**
After training the model with different techniques, we achieved the following results:
- **F1 Score (Test)**: 0.60 (exceeds the target of 0.59).
- **Accuracy (Test)**: 83%.
- **AUC-ROC (Test)**: 0.85.

These results demonstrate the model's strong performance in identifying customers at risk of leaving Beta Bank.

## How to Use

### 1. **Clone the Repository**
Clone the repository to your local machine:
```bash
git clone <repository_url>
