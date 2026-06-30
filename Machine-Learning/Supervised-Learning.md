# Supervised Learning

## What is Supervised Learning?

Supervised Learning is a type of Machine Learning where a model learns from **labeled data**.

Labeled data means the correct answer (target/output) is already available during training.

---

## Basic Idea

```text
Input (Features)
        +
Known Output (Label)
        ↓
Train Model
        ↓
Learn Pattern
        ↓
Predict New Outputs
```

---

## Real-World Example

### House Price Prediction

Training Data:

| House Size (sq ft) | Price |
|-------------------|--------|
| 1000 | 50 Lakh |
| 1500 | 75 Lakh |
| 2000 | 1 Crore |

Input:

```text
House Size
```

Output:

```text
House Price
```

The model learns the relationship between size and price.

---

# Why "Supervised"?

Because the model is supervised using correct answers.

Example:

```text
Question → Answer

Input → Output
```

The model learns from historical examples.

---

# Components of Supervised Learning

## Features (X)

Input variables used to make predictions.

Examples:

```text
Age
Salary
Credit Score
Vehicle Age
Claim Amount
```

---

## Target (y)

Output variable that the model predicts.

Examples:

```text
Fraud
Loan Approval
Claim Severity
House Price
```

---

# Mathematical Representation

```text
X → y
```

Where:

```text
X = Features

y = Target
```

Goal:

```text
Learn Function

f(X) = y
```

---

# Types of Supervised Learning

```text
Regression
Classification
```

---

# 1. Regression

## Theory

Regression predicts continuous numerical values.

---

Examples:

```text
House Price Prediction

Insurance Premium Prediction

Claim Amount Prediction

Sales Forecasting
```

---

Example:

Input:

```text
House Size
```

Output:

```text
₹75,00,000
```

---

Popular Algorithms:

```text
Linear Regression
Ridge Regression
Lasso Regression
ElasticNet
```

---

# 2. Classification

## Theory

Classification predicts categories or classes.

---

Examples:

```text
Spam / Not Spam

Fraud / Not Fraud

Disease / No Disease

Claim Approved / Rejected
```

---

Example:

Input:

```text
Claim Information
```

Output:

```text
Fraud
```

---

Popular Algorithms:

```text
Logistic Regression
Decision Tree
Random Forest
XGBoost
Naive Bayes
SVM
KNN
```

---

# Supervised Learning Workflow

```text
Collect Data
      ↓
Data Cleaning
      ↓
Feature Engineering
      ↓
Train-Test Split
      ↓
Model Training
      ↓
Prediction
      ↓
Evaluation
```

---

# Dataset Example

## Loan Approval

| Age | Salary | Approved |
|------|---------|-----------|
| 25 | 50000 | Yes |
| 30 | 70000 | No |
| 35 | 80000 | Yes |

---

Features:

```text
Age
Salary
```

Target:

```text
Approved
```

---

# Train-Test Split

Training Data:

```text
Used for Learning
```

Typically:

```text
80%
```

---

Testing Data:

```text
Used for Evaluation
```

Typically:

```text
20%
```

---

Visualization:

```text
Dataset
   │
   ├── Train (80%)
   │
   └── Test (20%)
```

---

# Model Training

During training:

```text
Input Data
      ↓
Prediction
      ↓
Calculate Error
      ↓
Update Parameters
      ↓
Learn Patterns
```

---

# Prediction

After training:

```text
New Data
      ↓
Model
      ↓
Prediction
```

---

Example:

```text
Age = 28

Salary = 60000
```

Prediction:

```text
Loan Approved
```

---

# Loss Function

## Theory

Measures prediction error.

---

Example:

Actual:

```text
100
```

Predicted:

```text
80
```

Error:

```text
20
```

---

Goal:

```text
Minimize Error
```

---

Common Loss Functions:

```text
Mean Squared Error (Regression)

Cross Entropy Loss (Classification)
```

---

# Model Evaluation

After training, evaluate performance.

---

# Classification Metrics

```text
Accuracy
Precision
Recall
F1 Score
ROC-AUC
```

---

# Regression Metrics

```text
MAE
MSE
RMSE
R² Score
```

---

# Accuracy

Formula:

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

# Overfitting

## Theory

Model memorizes training data.

---

Behavior:

```text
Very High Training Accuracy

Poor Testing Accuracy
```

---

Example:

```text
Memorization
Not Learning
```

---

# Underfitting

## Theory

Model fails to learn patterns.

---

Behavior:

```text
Poor Training Accuracy

Poor Testing Accuracy
```

---

# Good Fit

```text
Good Training Accuracy

Good Testing Accuracy
```

---

# Common Supervised Learning Algorithms

## Regression Algorithms

```text
Linear Regression
Polynomial Regression
Ridge Regression
Lasso Regression
ElasticNet
```

---

## Classification Algorithms

```text
Logistic Regression
Decision Tree
Random Forest
XGBoost
LightGBM
CatBoost
Naive Bayes
SVM
KNN
```

---

# Python Example

## Classification

```python
from sklearn.ensemble import RandomForestClassifier

model = RandomForestClassifier()

model.fit(
    X_train,
    y_train
)

predictions = model.predict(
    X_test
)
```

---

## Regression

```python
from sklearn.linear_model import LinearRegression

model = LinearRegression()

model.fit(
    X_train,
    y_train
)

prediction = model.predict(
    X_test
)
```

---

# Insurance Example

## Fraud Detection

Features:

```text
Claim Amount
Vehicle Age
Policy Age
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
Historical Claims
        ↓
Train Model
        ↓
Learn Patterns
        ↓
Predict Fraud
```

---

# Insurance Example 2

## Claim Severity Prediction

Features:

```text
Claim Amount
Accident Type
Vehicle Age
Driver History
```

Target:

```text
Claim Severity
```

Output:

```text
Low
Medium
High
```

---

# Advantages

```text
High Accuracy
Easy Evaluation
Widely Used
Large Number of Algorithms
Works Well With Historical Data
```

---

# Disadvantages

```text
Requires Labeled Data
Data Collection Can Be Expensive
Can Overfit
Needs Quality Data
```

---

# Real-World Applications

```text
Fraud Detection
Spam Detection
Credit Scoring
Insurance Risk Assessment
Medical Diagnosis
Price Prediction
Customer Churn Prediction
Recommendation Systems
```

---

# Interview Questions

### Q1. What is Supervised Learning?

```text
A machine learning approach where models learn from labeled data to predict outputs.
```

---

### Q2. What are Features?

```text
Input variables used by the model.
```

---

### Q3. What is a Target Variable?

```text
The output variable the model predicts.
```

---

### Q4. Difference between Regression and Classification?

```text
Regression:
Predicts numerical values.

Classification:
Predicts categories.
```

---

### Q5. What is Overfitting?

```text
When a model memorizes training data and performs poorly on unseen data.
```

---

# Learning Path

```text
Supervised Learning Basics
          ↓
Features & Labels
          ↓
Regression
          ↓
Classification
          ↓
Train-Test Split
          ↓
Loss Functions
          ↓
Evaluation Metrics
          ↓
Overfitting & Underfitting
          ↓
Scikit-Learn
          ↓
Real-World Projects
```

# Most Important Topics for AI Engineers

```text
Features
Labels
Regression
Classification
Train-Test Split
Loss Functions
Evaluation Metrics
Overfitting
Underfitting
Model Training
```

Supervised Learning is the foundation of most real-world Machine Learning systems, including:

```text
Fraud Detection
Claim Prediction
Credit Scoring
Customer Churn
Recommendation Systems
Medical AI
Predictive Analytics
```