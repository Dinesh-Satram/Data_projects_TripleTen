# Sentiment Analysis of Movie Reviews Using NLP and Machine Learning

## Project Overview

The Film Junky Union is developing a system for filtering and categorizing movie reviews. The goal of this project is to classify movie reviews as positive or negative based on a dataset of IMDb movie reviews. The model must achieve an F1 score of at least 0.85 on the test set. The system will help categorize user feedback and improve review analysis for movie enthusiasts.

## Data Description

The dataset is stored in the `imdb_reviews.tsv` file and contains the following fields:

- **review**: The review text.
- **pos**: The target variable, where '0' indicates a negative review and '1' indicates a positive review.
- **ds_part**: Indicates whether the review belongs to the 'train' or 'test' dataset.
- **Other Columns**: There are several additional columns, such as `title_type`, `genres`, and `rating`, but only the `review` and `pos` columns are used for the sentiment analysis.

## Project Steps

### 1. **Load and Inspect Data**
- The data is loaded from the `imdb_reviews.tsv` file.
- Initial inspection includes checking for missing values and duplicates. The dataset is clean and ready for analysis.

### 2. **Exploratory Data Analysis (EDA)**
- The number of reviews per movie and the distribution of ratings are analyzed.
- Sentiment distributions are explored, ensuring a balanced dataset with nearly equal numbers of positive and negative reviews.
- Visualizations are generated to analyze trends over the years and review distributions.

### 3. **Text Preprocessing**
- The review texts are normalized by converting them to lowercase, removing digits, punctuation, and stopwords.
- Various preprocessing methods are compared, including lemmatization using spaCy and text cleaning using regular expressions.

### 4. **Modeling**
- **Model 0 (Dummy Classifier)**: A baseline model using the most frequent class strategy.
- **Model 1 (TF-IDF + Logistic Regression)**: The first real model, using TF-IDF vectorization and Logistic Regression.
- **Model 2 (spaCy + TF-IDF + Logistic Regression)**: This model incorporates spaCy-based lemmatization and TF-IDF vectorization.
- **Model 3 (spaCy + TF-IDF + LightGBM)**: LightGBM is used as a more powerful classifier with the same preprocessing pipeline.
- **Model 4 (BERT)**: BERT embeddings were used for feature extraction, but due to computational limitations, it was not fully tested in this environment.

### 5. **Model Evaluation**
- Models are evaluated based on accuracy, F1 score, ROC AUC, and Average Precision Score (APS).
- The F1 score for each model is calculated on both the training and test datasets to determine its performance.
- The models are compared based on their performance metrics, and the best models are selected for further use.

### 6. **Model Comparison and Conclusion**
- **Model 1 (TF-IDF + Logistic Regression)**: Strong performance with an F1 score of 0.88 on the test set, meeting the project’s threshold.
- **Model 2 (spaCy + TF-IDF + Logistic Regression)**: Slightly better than Model 1, with F1 scores of 0.93 (train) and 0.88 (test).
- **Model 3 (spaCy + TF-IDF + LightGBM)**: Best performance with an F1 score of 0.96 on the train set, though there is slight overfitting on the test set with an F1 score of 0.87.
- **Model 4 (BERT)**: Not fully tested, but expected to improve performance significantly.

## Key Findings

| Model                         | Accuracy (Train) | Accuracy (Test) | F1 Score (Train) | F1 Score (Test) | APS (Train) | APS (Test) | ROC AUC (Train) | ROC AUC (Test) |
|-------------------------------|------------------|-----------------|------------------|-----------------|-------------|------------|-----------------|----------------|
| **Model 1 (TF-IDF + Logistic Regression)** | 0.92             | 0.88            | 0.92             | 0.88            | 0.97        | 0.95       | 0.97            | 0.95           |
| **Model 2 (spaCy + TF-IDF + Logistic Regression)** | 0.93             | 0.88            | 0.93             | 0.88            | 0.98        | 0.95       | 0.98            | 0.95           |
| **Model 3 (spaCy + TF-IDF + LightGBM)** | 0.96             | 0.87            | 0.96             | 0.87            | 0.99        | 0.94       | 0.99            | 0.94           |

- **Model 1** is the most efficient and well-performing model, offering strong accuracy and F1 scores without overfitting.
- **Model 2** shows slight improvements in text representation due to spaCy's lemmatization, with similar performance to Model 1.
- **Model 3** offers the highest performance but suffers from slight overfitting, as shown by the drop in performance on the test set.
- **Model 4 (BERT)** could improve contextual understanding but is computationally expensive and was not fully evaluated in this implementation.

## Conclusion

The best models for this task are **Model 1 (TF-IDF + Logistic Regression)** and **Model 2 (spaCy + TF-IDF + Logistic Regression)**. Both meet the F1 score requirement of 0.85, with **Model 1** offering the best overall balance between accuracy, efficiency, and generalization. **Model 3 (spaCy + TF-IDF + LightGBM)** provides the highest training performance but shows signs of overfitting. **BERT**, while potentially powerful, requires more computational resources than available in this project environment.

## How to Run the Project

### Prerequisites:
Install the required libraries:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn spacy lightgbm transformers nltk
