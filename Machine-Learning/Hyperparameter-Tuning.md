# Ensemble Learning

## What is Ensemble Learning?

Ensemble Learning is a Machine Learning technique that combines multiple models to create a stronger and more accurate model.

Basic Idea:

```text
Many Weak Models
       ↓
Combine Predictions
       ↓
Strong Model
```

---

# Why Ensemble Learning?

A single model may make mistakes.

Combining multiple models often provides:

```text
Higher Accuracy
Better Generalization
Reduced Overfitting
More Robust Predictions
```

---

# Real-Life Example

Suppose 5 doctors diagnose a patient.

Instead of trusting one doctor:

```text
Doctor 1
Doctor 2
Doctor 3
Doctor 4
Doctor 5
      ↓
Final Decision
```

Accuracy improves.

---

# Types of Ensemble Learning

```text
Bagging
Boosting
Stacking
```

---

# 1. Bagging

## Theory

Bagging stands for:

```text
Bootstrap Aggregating
```

Multiple models are trained independently.

---

Workflow:

```text
Dataset
    ↓
Model 1

Model 2

Model 3

Model 4
    ↓
Voting / Averaging
    ↓
Final Prediction
```

---

# Random Forest

Most popular Bagging algorithm.

---

Structure:

```text
Tree 1

Tree 2

Tree 3

Tree 4
```

---

Classification:

```text
Majority Voting
```

---

Regression:

```text
Average Prediction
```

---

## Python Example

```python
from sklearn.ensemble import RandomForestClassifier

model = RandomForestClassifier(
    n_estimators=100
)

model.fit(X_train, y_train)
```

---

# Advantages

```text
High Accuracy
Less Overfitting
Handles Large Datasets
```

---

# 2. Boosting

## Theory

Boosting trains models sequentially.

Each model learns from previous mistakes.

---

Workflow:

```text
Model 1
    ↓
Find Errors
    ↓
Model 2
    ↓
Find Errors
    ↓
Model 3
```

---

Goal:

```text
Reduce Error Iteratively
```

---

# Popular Boosting Algorithms

```text
AdaBoost
Gradient Boosting
XGBoost
LightGBM
CatBoost
```

---

# XGBoost

Most popular boosting algorithm.

---

Benefits:

```text
Fast
Accurate
Handles Missing Values
```

---

Applications:

```text
Fraud Detection
Credit Scoring
Insurance Analytics
```

---

## Python Example

```python
from xgboost import XGBClassifier

model = XGBClassifier()

model.fit(X_train, y_train)
```

---

# 3. Stacking

## Theory

Combines predictions from multiple models.

---

Workflow:

```text
Random Forest

XGBoost

SVM
      ↓
Meta Model
      ↓
Final Prediction
```

---

Benefits:

```text
Higher Performance
Combines Strengths
```

---

# Ensemble Learning Summary

| Method | Training Style |
|----------|---------------|
| Bagging | Parallel |
| Boosting | Sequential |
| Stacking | Multi-Level |

---

# Model Evaluation

## What is Model Evaluation?

Model Evaluation measures how well a machine learning model performs on unseen data.

---

Goal:

```text
Check Model Quality
```

---

# Why Evaluate Models?

Without evaluation:

```text
No Idea If Model Works
```

---

# Train-Test Split

```text
Dataset
   │
   ├── Train Data (80%)
   │
   └── Test Data (20%)
```

---

Training:

```text
Learn Patterns
```

Testing:

```text
Measure Performance
```

---

# Classification Metrics

## Accuracy

### Formula

```text
Correct Predictions
-------------------
Total Predictions
```

---

Example:

```text
95 Correct

100 Total
```

Accuracy:

```text
95%
```

---

# Confusion Matrix

| | Pred Yes | Pred No |
|----|----|----|
| Actual Yes | TP | FN |
| Actual No | FP | TN |

---

Definitions:

```text
TP = True Positive

TN = True Negative

FP = False Positive

FN = False Negative
```

---

# Precision

Measures:

```text
How many predicted positives were correct?
```

---

Formula:

```text
TP
--------
TP + FP
```

---

# Recall

Measures:

```text
How many actual positives were detected?
```

---

Formula:

```text
TP
--------
TP + FN
```

---

# F1 Score

Balance between:

```text
Precision
Recall
```

---

Formula:

```text
2 × Precision × Recall
-----------------------
 Precision + Recall
```

---

# ROC-AUC

Measures classification quality.

---

Range:

```text
0.5 = Random

1.0 = Perfect
```

---

# Regression Metrics

## MAE

Mean Absolute Error

---

Formula:

```text
Average Absolute Error
```

---

# MSE

Mean Squared Error

---

Formula:

```text
Average Squared Error
```

---

# RMSE

Root Mean Squared Error

---

Formula:

```text
√MSE
```

---

# R² Score

Measures:

```text
How Much Variance Is Explained
```

---

Range:

```text
0 to 1
```

---

# Hyperparameter Tuning

## What are Hyperparameters?

Parameters set before model training.

---

Examples:

```text
Learning Rate

Batch Size

Number of Trees

Maximum Depth

K Value
```

---

# Why Tune Hyperparameters?

Default values may not be optimal.

Goal:

```text
Find Best Settings
```

---

# Example

Random Forest:

```python
RandomForestClassifier(
    n_estimators=100,
    max_depth=10
)
```

---

Hyperparameters:

```text
n_estimators

max_depth
```

---

# Grid Search

## Theory

Tests every possible combination.

---

Example

```python
params = {

    "n_estimators":[100,200],

    "max_depth":[5,10]
}
```

---

Combinations:

```text
100,5

100,10

200,5

200,10
```

---

Best combination selected automatically.

---

## Python Example

```python
from sklearn.model_selection import GridSearchCV

grid = GridSearchCV(
    model,
    params,
    cv=5
)

grid.fit(
    X_train,
    y_train
)

print(
    grid.best_params_
)
```

---

# Random Search

## Theory

Randomly selects combinations.

---

Advantages:

```text
Faster
Less Expensive
```

---

## Python Example

```python
from sklearn.model_selection import RandomizedSearchCV
```

---

# Cross Validation

## Theory

Evaluates model multiple times.

---

Example:

```text
5-Fold Cross Validation
```

---

Workflow:

```text
Fold 1 → Test

Fold 2 → Test

Fold 3 → Test

Fold 4 → Test

Fold 5 → Test
```

---

Benefits:

```text
Reliable Evaluation
Less Variance
```

---

# Scikit-Learn

## What is Scikit-Learn?

Scikit-Learn is the most widely used Machine Learning library in Python.

Official website:

:contentReference[oaicite:0]{index=0}

---

# Why Scikit-Learn?

Provides:

```text
Data Preprocessing
Feature Engineering
Machine Learning Models
Evaluation Metrics
Hyperparameter Tuning
```

---

# Common Modules

## Train-Test Split

```python
from sklearn.model_selection import train_test_split
```

---

## Linear Regression

```python
from sklearn.linear_model import LinearRegression
```

---

## Logistic Regression

```python
from sklearn.linear_model import LogisticRegression
```

---

## Random Forest

```python
from sklearn.ensemble import RandomForestClassifier
```

---

## K-Means

```python
from sklearn.cluster import KMeans
```

---

## Metrics

```python
from sklearn.metrics import accuracy_score
```

---

# Complete Scikit-Learn Workflow

```python
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)

model = RandomForestClassifier()

model.fit(
    X_train,
    y_train
)

predictions = model.predict(
    X_test
)

accuracy = accuracy_score(
    y_test,
    predictions
)

print(accuracy)
```

---

# Insurance Example

## Fraud Detection

Features:

```text
Claim Amount
Policy Age
Vehicle Age
Driver Age
```

Target:

```text
Fraud
Not Fraud
```

---

Workflow:

```text
Data Cleaning
      ↓
Feature Engineering
      ↓
Train-Test Split
      ↓
Random Forest / XGBoost
      ↓
Model Evaluation
      ↓
Hyperparameter Tuning
      ↓
Deployment
```

---

# Interview Questions

### Q1. What is Ensemble Learning?

```text
A technique that combines multiple models to improve prediction performance.
```

---

### Q2. Difference between Bagging and Boosting?

```text
Bagging:
Parallel Training

Boosting:
Sequential Training
```

---

### Q3. What is Hyperparameter Tuning?

```text
The process of finding the best model settings before training.
```

---

### Q4. What is Cross Validation?

```text
A technique that evaluates model performance using multiple train-test splits.
```

---

### Q5. What is Scikit-Learn?

```text
A Python library for machine learning, preprocessing, evaluation, and model selection.
```

---

# Learning Path

```text
Ensemble Learning
      ↓
Random Forest
      ↓
Boosting
      ↓
XGBoost
      ↓
Model Evaluation
      ↓
Confusion Matrix
      ↓
Cross Validation
      ↓
Hyperparameter Tuning
      ↓
Grid Search
      ↓
Scikit-Learn
```

# Most Important Topics for AI Engineers

```text
Random Forest
XGBoost
Bagging
Boosting
Accuracy
Precision
Recall
F1 Score
ROC-AUC
Cross Validation
Grid Search
Random Search
Scikit-Learn
```

These concepts are heavily used in:

```text
Fraud Detection
Claim Prediction
Customer Churn
Risk Modeling
Recommendation Systems
Insurance Analytics
MLOps
AI Engineering
```