# Megaline Mobile Plan Recommendation System

## Project Overview

Megaline, a mobile carrier, aims to improve customer satisfaction and revenue by encouraging subscribers to switch from legacy plans to newer offerings: Smart or Ultra. The objective of this project is to develop a classification model that accurately predicts whether a subscriber is better suited for the Smart or Ultra mobile plan based on their monthly usage behavior.

The main goal is to develop a machine learning model with a high accuracy rate (threshold: 75%) that can be used to recommend the most appropriate mobile plan for Megaline’s subscribers.

## Project Structure



- **README.md**: This file with project description, setup instructions, and results.
- **mobile_plan_recommendation.ipynb**: Jupyter notebook containing the steps for data exploration, model training, evaluation, and testing.
- **datasets/users_behavior.csv**: CSV file containing subscribers' monthly usage data.
- **models/random_forest_model.pkl**: A saved RandomForest model for easy deployment (optional).

## Project Description

### 1. **Data Exploration**
The dataset contains monthly usage behavior of subscribers, with the following columns:
- **calls**: Number of calls made during the month
- **minutes**: Total duration of calls in minutes
- **messages**: Number of text messages sent
- **mb_used**: Internet traffic used in MB
- **is_ultra**: Plan for the current month (1 for Ultra, 0 for Smart)

After loading and exploring the data, the dataset was confirmed to be clean with no missing values.

### 2. **Data Preprocessing**
The data was split into three sets:
- **Training Set**: 60% of the data used to train the models.
- **Validation Set**: 20% of the data used to tune the hyperparameters.
- **Test Set**: 20% of the data used to evaluate model performance.

The dataset was split using `train_test_split` from `sklearn`.

### 3. **Model Selection**
Three models were evaluated for the classification task:
- **DecisionTreeClassifier**
- **RandomForestClassifier**
- **LogisticRegression**

#### Hyperparameter Tuning:
- **DecisionTreeClassifier**: Tuned by changing the `max_depth` parameter.
- **RandomForestClassifier**: Tuned by changing both `n_estimators` and `max_depth`.
- **LogisticRegression**: Tuned by adjusting the solver and regularization.

The RandomForestClassifier emerged as the best-performing model with the highest accuracy. The best hyperparameters were:
- **n_estimators = 40**
- **max_depth = 8**

### 4. **Model Evaluation**
The RandomForestClassifier achieved a validation accuracy of 80.9% and a test accuracy of 79.6%, both surpassing the required threshold of 75%.

#### Baseline Model Accuracy:
- **Predicting all users as 'Smart'**: 68.43% accuracy.
- **Predicting all users as 'Ultra'**: 31.57% accuracy.

These baseline accuracies highlight the significant improvement achieved by the RandomForestClassifier.

### 5. **Sanity Check**
A sanity check was performed to compare the model's accuracy with two baseline approaches:
- **Predicting all users as Smart** (accuracy: 68.43%).
- **Predicting all users as Ultra** (accuracy: 31.57%).

The RandomForestClassifier outperformed both of these baseline models, confirming its effectiveness in predicting the most suitable plan.

### 6. **Conclusion**
The RandomForestClassifier with the optimal hyperparameters was selected as the final model. It provides accurate recommendations for Megaline subscribers, helping them transition to the most appropriate mobile plans. This model can be deployed to improve customer satisfaction and optimize revenue.

## How to Use

### 1. **Clone the Repository**
Clone the repository to your local machine:
```bash
git clone <repository_url>
