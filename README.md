# INT303-Student-Performance-Prediction

## Table of Contents
- [Introduction](#introduction)
- [Dataset Description](#dataset-description)
- [Methodology](#methodology)
- [Results and Discussion](#results-and-discussion)
- [Future Improvements](#future-improvements)

---

## Introduction
This project aims to predict student retention and academic success (Dropout, Enrolled, or Graduate) using machine learning techniques. By analyzing demographic, academic, and behavioral data, we develop a robust classification model to enhance decision-making in educational institutions. The project involves Exploratory Data Analysis (EDA), feature engineering, and predictive modeling.

---

## Dataset Description
The dataset consists of several key features categorized into different groups:

### Demographic Information
- **Age at enrollment**
- **Gender**
- **Nationality**

### Academic Performance
- **Grades from the first and second semesters**
- **GPA calculations**
- **Pass rates and failed subjects**

### Behavioral and Social Data
- **Attendance records**
- **Participation in extracurricular activities**
- **Financial aid and scholarship status**

### Target Variables
- **Dropout (2)**: The student has withdrawn from the program.
- **Enrolled (0)**: The student remains in the program but has not graduated.
- **Graduate (1)**: The student has successfully completed the program.


## Methodology

### 1. Exploratory Data Analysis (EDA)
- Identified key predictive features using correlation analysis.
- Found that **academic performance features** had the strongest correlation with student outcomes.
- Created additional features such as **pass rate**, **average grade**, and **economic stress**.
<img width="350" alt="Screenshot 2025-02-23 at 16 55 05" src="https://github.com/user-attachments/assets/fcb2c654-50c2-4e95-9ae1-e32dfdf21221" />
<img width="350" alt="Screenshot 2025-02-23 at 16 55 52" src="https://github.com/user-attachments/assets/a5a108ae-ed66-46d1-9789-c5461de94b3d" />
<img width="744" alt="Screenshot 2025-02-23 at 16 55 37" src="https://github.com/user-attachments/assets/0e9d3728-3f95-47c6-aa37-f283e5e5302f" />

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
- Achieved an **accuracy of 86.41%**.
- Classification report:

| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| 0 (Enrolled) | 0.87 | 0.85 | 0.86 | 355 |
| 1 (Graduate) | 0.83 | 0.92 | 0.87 | 356 |
| 2 (Dropout) | 0.90 | 0.83 | 0.86 | 356 |
| **Accuracy** |  |  | **0.86** | **1067** |
| **Macro Avg** | 0.87 | 0.86 | 0.86 | 1067 |
| **Weighted Avg** | 0.87 | 0.86 | 0.86 | 1067 |
<img width="500" alt="Screenshot 2025-02-23 at 16 59 20" src="https://github.com/user-attachments/assets/a5917770-1fd4-4def-843e-22dbac9ad128" />

- **ROC-AUC Score: 0.95** (high prediction reliability).
<img width="500" alt="Screenshot 2025-02-23 at 16 59 44" src="https://github.com/user-attachments/assets/a991741a-7a2c-4668-abc6-daa156be818c" />

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
