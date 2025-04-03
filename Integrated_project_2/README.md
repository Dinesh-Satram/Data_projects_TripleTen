# Optimizing Gold Recovery Efficiency Using Machine Learning: A Data-Driven Approach

## Project Overview
Gold mining operations face challenges in efficiently extracting gold due to fluctuations in raw material composition and processing conditions. This project leverages historical data from the extraction and purification processes to develop a machine learning model that predicts gold recovery efficiency. By applying data preprocessing, exploratory analysis, and machine learning, the project aims to enhance the decision-making process, minimize losses, and improve overall operational efficiency.

## Project Structure
1. **Introduction**
2. **Data Preprocessing**
3. **Data Analysis**
4. **Model Development**
5. **Final Model Evaluation**
6. **Findings and Conclusion**

## 1. Introduction
The goal of this project is to predict gold recovery rates during various stages of the flotation process. We aim to build a model that can predict recovery efficiency based on available data, allowing mining companies to optimize their extraction processes and maximize gold yield.

This project involves:
- Data preprocessing and cleaning
- Exploratory data analysis (EDA)
- Feature engineering and selection
- Model training using Random Forest and Linear Regression
- Hyperparameter tuning and final evaluation
- Comparison with a dummy model for benchmarking

## 2. Data Preprocessing

### Datasets
The following datasets were used:
- **gold_recovery_train.csv** — Training dataset containing historical data with features and target variables.
- **gold_recovery_test.csv** — Test dataset without target variables.
- **gold_recovery_full.csv** — Complete dataset containing all features, including those missing in the test set.

The data includes multiple features, such as concentration values for metals (Au, Ag, Pb) at various stages of the flotation process, and process parameters like air flow and levels.

### Data Cleaning Steps
1. **Missing Values**: Missing values were filled using forward fill (`ffill`) due to the ordered nature of the data.
2. **Duplicate Rows**: Duplicate rows were removed from both the training and test datasets.
3. **Feature Selection**: Only the features present in the test dataset were used to train the models, ensuring compatibility with production data.
4. **Recovery Calculation Validation**: The recovery formula was validated using the training data, with a Mean Absolute Error (MAE) of 0.0000, confirming that the dataset's "rougher.output.recovery" values were consistent with the calculation.

## 3. Data Analysis

### Metal Concentration Changes Across Processing Stages
We analyzed the concentration changes of metals (Au, Ag, Pb) at different stages of the flotation process:
- **Gold (Au)**: Concentration increases from the raw feed to the final concentrate.
- **Silver (Ag)** and **Lead (Pb)**: Show decreasing trends as they are removed from the concentrate during processing.

### Feed Particle Size Distribution
A comparison between the training and test datasets showed that the particle size distribution was consistent, with only slight differences in lower particle sizes, ensuring that the model won't face significant issues due to feed size discrepancies.

### Total Concentration Analysis
The analysis of total concentrations of metals at various stages revealed that concentration increases through each stage, as expected, with anomalies found in the form of zero values in the dataset. These rows were removed to ensure data integrity.

## 4. Model Development

### Evaluation Metric
The main evaluation metric for this project is **sMAPE** (Symmetric Mean Absolute Percentage Error), which combines the errors from both the "rougher.output.recovery" and "final.output.recovery" features.

### Model Training
Two models were trained:
1. **Linear Regression**: A simple model used for baseline performance.
2. **Random Forest Regressor**: A more complex model expected to perform better due to its ability to handle non-linear relationships.

### Hyperparameter Tuning
Random Forest hyperparameters were tuned using **RandomizedSearchCV** to find the best model. The best hyperparameters found were:
- `n_estimators`: 100
- `max_depth`: 15
- `min_samples_split`: 10
- `min_samples_leaf`: 4
- `max_features`: 'log2'

## 5. Final Model Evaluation

### Model Evaluation on Test Data
The trained Random Forest model was evaluated on the test dataset, achieving an sMAPE score of **12.2285**. Surprisingly, this model performed worse than a simple dummy model, which achieved an sMAPE score of **9.3613**, indicating the challenge in capturing meaningful patterns from the available data.

### Model Limitations
- The model's performance did not exceed that of a constant model (Dummy Regressor), indicating potential issues with feature selection, hyperparameter tuning, or model complexity.
- Future improvements may involve trying other models (e.g., Gradient Boosting) and refining feature engineering.

## 6. Findings and Conclusion

### Key Findings:
- **Data Cleaning**: Duplicates were removed, and missing values were filled using forward fill, ensuring the data was clean for model training.
- **Exploratory Data Analysis (EDA)**: Gold concentration increased across the stages, while silver and lead concentrations decreased. Feed particle size distributions were consistent between the training and test datasets.
- **Model Performance**: The Random Forest model underperformed compared to the Dummy Regressor, suggesting that additional steps like advanced feature engineering or alternative models are necessary.
- **sMAPE Evaluation**: The final model achieved a relatively high sMAPE value, indicating that the model's predictions were not highly accurate.

### Conclusion:
Despite a structured approach and model development, the Random Forest model did not outperform a simple dummy model, highlighting the difficulty of capturing meaningful patterns in the gold recovery dataset. Future work may involve further refining the models, experimenting with other algorithms, and improving feature selection and engineering.

## How to Run the Project

### Prerequisites:
Install the required libraries:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy
