# Stroke Prediction & Analysis 

## Project Overview
This project focuses on predicting the likelihood of stroke events based on patient data (age, BMI, glucose levels, etc.) using Machine Learning techniques.
Beyond standard modeling, the analysis includes **deep statistical testing**, **imbalanced data handling**, and **SQL queries**.

## Technologies used
 **Python** (Pandas, NumPy)
 **Machine Learning** (Scikit-learn, Random Forest)
 **Data Visualization** (Seaborn, Matplotlib)
 **Statistics** (SciPy - Mann-Whitney U, Shapiro-Wilk)
 **SQL** (SQLite within Python for Data Validation)

## Workflow & Methodology

### 1. ETL and EDA
 Handled missing values in `bmi` and `smoking_status`.
 Visualized distributions and correlations.
 **Statistical Insight:** Used **Mann-Whitney U test** instead of T-test for glucose levels, as the Shapiro-Wilk test confirmed non-normal distribution (p < 0.05).

### 2. Handling Imbalanced Data
 The original dataset was highly imbalanced (approx. 95% non-stroke vs. 5% stroke).
 Implemented **Undersampling** to create a balanced dataset for fair model training, preventing the model from being biased towards the majority class.

### 3. Machine Learning Modeling
 Trained a **Random Forest Classifier**.
 Optimized hyperparameters using **GridSearchCV** (tuning `n_estimators`, `max_depth`, etc.).
 **Business Logic:** Adjusted the prediction **threshold to 30%** (instead of the default 50%) to prioritize **Recall**. In a context like this, minimizing False Negatives (missing a stroke patient) is more critical than False Positives.

### 4. SQL (Business Simulation)
 Used **SQL queries** directly into the workflow to answer business questions.
 SQL concepts used:
     WINDOW Functions (RANK, LAG, SUM OVER)
     CTEs (Common Table Expressions)
     

## Key Findings
 **Age** is the most significant predictor of stroke.
 While **BMI** is a risk factor, the relationship is non-linear (U-shaped, low and high are both at high risk), and age often acts as a confounding variable.
 **Glucose levels** show a statistically significant difference between stroke and non-stroke groups.

---
*Created by Szabolcs - 2026*
