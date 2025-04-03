# Age Prediction Using Deep Learning for Alcohol Sales Regulation

## Project Overview

The objective of this project is to build a deep learning model to predict the age of a person from their photograph. The supermarket chain, Good Seed, seeks to ensure compliance with alcohol sales regulations by verifying that customers are above the legal drinking age before selling alcohol to them. This model leverages computer vision techniques using a pre-trained ResNet50 model to predict the age of individuals from facial images, assisting in verifying the customer's age.

## Data Description

The dataset used for this project is stored in the `/datasets/faces/` directory and includes:

- **final_files**: A folder containing over 7,500 images of faces.
- **labels.csv**: A CSV file that contains the file names and corresponding real ages of individuals in the images.

The goal is to train a model to predict the age of a person in the images, which is crucial for ensuring that the supermarket does not sell alcohol to underage individuals.

## Project Steps

### 1. **Data Loading and Preprocessing**
- **Images**: The images are loaded using the `ImageDataGenerator` class, with data augmentation (rotation, width/height shift, horizontal flip) applied to the training data.
- **Labels**: The age labels are loaded from the `labels.csv` file, which corresponds to the ages of the individuals in the images.

### 2. **Exploratory Data Analysis (EDA)**
- The age distribution is visualized to understand the spread of ages in the dataset.
- Sample images from different age groups are displayed to examine the diversity of the dataset in terms of age and image quality.

### 3. **Model Architecture**
- A transfer learning approach is used, where a pre-trained ResNet50 model (from ImageNet) is used as a feature extractor. The model is fine-tuned by adding custom layers for regression tasks.
- The architecture includes a **GlobalAveragePooling2D** layer, a **Dropout** layer, and a **Dense** layer to predict the age.

### 4. **Model Training**
- The model is trained using the Adam optimizer with a learning rate of 0.0005, using the **Mean Squared Error (MSE)** loss function, and the **Mean Absolute Error (MAE)** metric to evaluate performance.
- The model is trained for 20 epochs, with the training and validation datasets being separated using an 80/20 split.

### 5. **Model Evaluation**
- The final validation MAE is evaluated to determine the model's performance. The target is to achieve an MAE score of less than 8.

### 6. **Results**
The training and validation results show that the model has improved across epochs, with the final training MAE of 2.2401 and validation MAE of 7.0685, indicating the model is able to predict age with acceptable accuracy.

### 7. **Conclusions**
- **Model Performance**: The model achieved a validation MAE below the required threshold of 8, making it suitable for deployment in real-world scenarios.
- **Recommendations for Improvement**:
  - More diverse data augmentation and acquiring more samples of older individuals could help improve accuracy for older age groups.
  - Experimenting with other pre-trained models, such as EfficientNet or InceptionNet, could further enhance performance.

## Model Training Results

### Training and Validation Loss (MSE) and MAE (Mean Absolute Error):

| Epoch | Training Loss (MSE) | Training MAE | Validation Loss (MSE) | Validation MAE |
|-------|---------------------|--------------|-----------------------|----------------|
| 1     | 201.6916            | 10.5523      | 547.0254              | 18.3539        |
| 20    | 8.5300              | 2.2401       | 89.4965               | 7.0685         |

### Analysis:
- The model shows a significant reduction in loss over the training epochs, which indicates effective learning.
- The validation MAE of 7.0685 is below the acceptable threshold of 8, which suggests that the model is accurate enough to be used for age verification purposes.

## Usefulness of the Model

This model can be deployed in supermarkets and retail stores to verify the age of customers purchasing alcohol, ensuring compliance with age-related laws. It could also be used for demographic analysis in customer research.

### Practical Applications:
- **Age Verification for Alcohol Sales**: The model can be used to automate the age verification process at checkout counters in supermarkets.
- **Demographic Insights**: Retailers can use the model for understanding customer demographics based on age, which can help with targeted marketing and product recommendations.

## Limitations and Challenges

- **Data Imbalance**: The dataset is skewed towards younger individuals, which could cause the model to be less accurate for predicting ages of older individuals.
- **Image Quality Variability**: Low-quality images, such as those with poor lighting or rotations, may reduce model performance.
- **Generalization Issues**: The model might not generalize well to diverse ethnicities and environments if the dataset does not adequately represent those variations.

## Next Steps and Recommendations

- **Data Augmentation**: Further augmenting the dataset with more variations in age and environment could help improve performance.
- **Ethnicity and Background Consideration**: Collecting more diverse samples in terms of ethnicities and backgrounds could improve the model’s robustness and generalization capabilities.
- **Fine-tuning the Model**: Trying different architectures and fine-tuning the ResNet50 model more extensively might lead to improved performance.

## How to Run the Project

### Prerequisites:
Install the required libraries:
```bash
pip install tensorflow pandas matplotlib
