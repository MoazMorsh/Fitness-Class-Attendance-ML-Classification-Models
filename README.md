
# Fitness Class Attendance Prediction

A machine learning classification project that predicts whether a member will attend a fitness class or not.

## Project Overview

The goal of this project is to build and evaluate classification models for **fitness class attendance prediction** using a structured workflow that includes:

- data loading and inspection
- data cleaning and preprocessing
- handling missing values and inconsistent formats
- exploratory analysis
- feature preparation
- model training and evaluation
- final model comparison and recommendation

This project was built as an end-to-end practice case for applying data preprocessing and machine learning classification techniques on tabular data.

---

## Problem Statement

The target variable is:

- `0` = Not Attended
- `1` = Attended

This makes the problem a **binary classification task**.

---

## Dataset Information

The dataset contains **1500 rows** and originally **8 columns**.

### Main features
- `months_as_member`
- `weight`
- `days_before`
- `day_of_week`
- `time`
- `category`

### Target
- `attended`

### Initial issues found
- missing values in `weight`
- inconsistent formatting in `days_before`
- inconsistent formatting in `day_of_week`
- categorical text values in `time`
- unclear category value `-`

---

## Data Cleaning and Preprocessing

The following preprocessing steps were applied:

- removed `booking_id` because it is only an identifier
- cleaned `days_before` by removing the word `"days"` and converting the column to integer
- standardized `day_of_week` to 3-letter weekday format
- encoded `time`:
  - `AM = 1`
  - `PM = 2`
- replaced `-` in `category` with `unknown`
- filled missing values in `weight` using the median
- checked duplicate rows

### Final cleaned dataset
- **1500 rows**
- **7 columns**
- **no missing values**

---

## Exploratory Findings

Some key observations from the dataset:

- average membership duration: **14.53 months**
- average weight: **75.18**
- average booking lead time: **8.35 days**
- attendance rate: about **30.3%**

### Class distribution
- Not Attended (`0`): **1046**
- Attended (`1`): **454**

This indicates a **slightly imbalanced dataset**, so evaluation metrics beyond accuracy are important.

---

## Feature Engineering and Preparation

### Numeric features
- `months_as_member`
- `weight`
- `days_before`
- `time`

### Categorical features
- `day_of_week`
- `category`

### Preprocessing pipeline
- **Numeric data**
  - median imputation
  - standard scaling
- **Categorical data**
  - most frequent imputation
  - one-hot encoding

### Train-test split
- training set: **80%**
- testing set: **20%**
- stratified split used to preserve class proportions

---

## Models Used

The following machine learning models were trained and evaluated:

- **K-Nearest Neighbors (KNN)**
- **Decision Tree**
- **Support Vector Machine (SVM)**
- **Naive Bayes**

---

## Model Results

| Model | Accuracy | Precision | Recall | F1-score |
|------|---------:|----------:|-------:|---------:|
| Naive Bayes | 0.7833 | 0.6512 | 0.6154 | 0.6328 |
| Decision Tree | 0.7933 | 0.7101 | 0.5385 | 0.6125 |
| SVM | 0.7967 | 0.7885 | 0.4505 | 0.5734 |
| KNN | 0.7667 | 0.6479 | 0.5055 | 0.5679 |

---

## Best Model

### Based on the main split result
**Naive Bayes** achieved the highest **F1-score**, making it the best model on the 80/20 train-test split.

### Based on practical judgment
**Decision Tree** appears to be the more reliable practical choice because:

- its performance was close to Naive Bayes
- it is easier to interpret
- it showed stronger stability when the test size was changed

### Additional note
When the test size was changed to **0.3** and **0.4**, the most stable model was the **Decision Tree**.

---

## Key Takeaways

- Data cleaning had a major impact on model readiness
- Accuracy alone was not enough because the dataset was imbalanced
- F1-score provided a better basis for model comparison
- Naive Bayes performed best on the main split
- Decision Tree appeared more stable and interpretable overall

---

## Tech Stack

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn

---

## Project Workflow

1. Load dataset
2. Inspect structure and data types
3. Clean inconsistent columns
4. Handle missing values
5. Prepare numeric and categorical pipelines
6. Split the data into training and testing sets
7. Train multiple classification models
8. Evaluate each model using:
   - Accuracy
   - Precision
   - Recall
   - F1-score
9. Compare results and select the most suitable model

---

## Repository Structure

```bash
.
├── README.md
├── fitness_class_2212.csv
├── Fitness Class Attendance.ipynb
└── assets/   # optional for images or charts
