# INT303-Student-Performance-Prediction

## Table of Contents
- [Introduction](#introduction)
- [Dataset](#dataset)
- [Methodology](#methodology)
- [Results and Discussion](#results-and-discussion)
- [Future Improvements](#future-improvements)

## Introduction
This project is part of the **Student Performance and Retention Prediction Competition**. The goal is to predict student outcomes (Dropout, Enrolled, or Graduate) using machine learning techniques based on demographic, academic, and behavioral data. This project includes Exploratory Data Analysis (EDA), data preprocessing, model building, and evaluation.

## Dataset

The dataset is sourced from a higher education institution and consists of the following features:

- **Demographic Information**: Age, gender, socio-economic background.
- **Academic Performance**: Grades and results from the first two semesters.
- **Behavioral and Social Data**: Attendance records, participation in extracurricular activities.

The target variable is the student's academic status:
- **Dropout**: The student has withdrawn from the program.
- **Enrolled**: The student remains in the program but has not graduated.
- **Graduate**: The student has successfully completed the program.

## Methodology

### 1. Exploratory Data Analysis (EDA)
- Identified key predictive features using correlation analysis.
- Found that **academic performance features** had the strongest correlation with student outcomes.
- Created additional features such as **pass rate**, **average grade**, and **economic stress**.

### 2. Data Preprocessing
- Encoded categorical variables.
- Checked and handled missing values (used median imputation as a precaution).
- Balanced the dataset using **SMOTE** to address class imbalance.
- Normalized numerical features.

### 3. Model Selection and Training
- Implemented a **Voting Classifier**, combining multiple models:
  - **Random Forest**
  - **XGBoost**
  - **LightGBM**
  - **HistGradientBoosting**
  - **MLP (Multi-layer Perceptron)**
- Tuned hyperparameters using **GridSearchCV** and **RandomizedSearchCV**.
- Applied **K-fold cross-validation** to improve generalization.

### 4. Evaluation
- Achieved an **accuracy of 86.13%**.
- **F1-score for each class**:
  - Enrolled: **0.85**
  - Graduate: **0.87**
  - Dropout: **0.86**
- **ROC-AUC Score: 0.95** (high prediction reliability).
- Identified **feature importance**, with academic performance being the most significant predictor.

## Results and Discussion
- **Strengths**:
  - The **Voting Classifier** improves robustness by combining multiple models.
  - High **accuracy and F1-score** across all classes.
- **Limitations**:
  - Feature overlap led to some misclassification between Dropout and Enrolled students.
  - Balancing techniques could introduce some noise or bias.
  - The model lacks interpretability due to its complexity.

## Future Improvements
- Optimize feature engineering to reduce class overlap.
- Explore additional **ensemble learning techniques**.
- Improve interpretability using **SHAP** or **LIME**.
- Experiment with other balancing techniques like **class-weight adjustments**.
