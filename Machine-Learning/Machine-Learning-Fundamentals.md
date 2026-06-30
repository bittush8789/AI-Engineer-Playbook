# Machine Learning Fundamentals

## What is Machine Learning?

Machine Learning (ML) is a branch of Artificial Intelligence (AI) that enables computers to learn patterns from data and make predictions or decisions without being explicitly programmed.

Traditional Programming:

```text
Input + Rules
        ↓
Output
```

Machine Learning:

```text
Input + Output Data
        ↓
Learning Algorithm
        ↓
Model
        ↓
Predictions
```

---

# Why Machine Learning?

Real-world problems often have too many rules to program manually.

Examples:

```text
Fraud Detection
Claim Severity Prediction
Spam Detection
Recommendation Systems
Customer Churn Prediction
Medical Diagnosis
```

Instead of writing rules, ML learns patterns automatically.

---

# Real-World Example

## Insurance Claim Prediction

Input:

```text
Driver Age
Vehicle Age
Claim Amount
Accident History
```

Output:

```text
High Risk
Low Risk
```

Machine Learning learns from historical claims and predicts future risk.

---

# Types of Machine Learning

```text
Supervised Learning
Unsupervised Learning
Reinforcement Learning
```

---

# 1. Supervised Learning

## Theory

The model learns from labeled data.

---

Example:

| Age | Salary | Loan Approved |
|------|---------|---------------|
| 25 | 50000 | Yes |
| 30 | 70000 | No |

---

Input:

```text
Age
Salary
```

Output:

```text
Loan Approved
```

---

Goal:

```text
Learn Relationship
```

between inputs and outputs.

---

Applications:

```text
Fraud Detection
Spam Detection
Price Prediction
Risk Prediction
```

---

# 2. Unsupervised Learning

## Theory

The model learns patterns from unlabeled data.

---

Example:

| Customer |
|-----------|
| A |
| B |
| C |

No labels available.

---

Goal:

```text
Find Hidden Patterns
```

---

Applications:

```text
Customer Segmentation
Market Basket Analysis
Anomaly Detection
```

---

# 3. Reinforcement Learning

## Theory

An agent learns through rewards and penalties.

---

Example:

```text
Robot Navigation
Game Playing
Autonomous Vehicles
```

---

Workflow:

```text
Agent
   ↓
Action
   ↓
Environment
   ↓
Reward
```

---

# Key Components of Machine Learning

```text
Data
Features
Labels
Model
Training
Prediction
Evaluation
```

---

# Dataset

## Theory

A collection of data used for learning.

---

Example:

| Age | Salary | Purchased |
|------|---------|------------|
| 25 | 50000 | Yes |
| 30 | 70000 | No |

---

# Features

## Theory

Input variables used for prediction.

---

Example:

```text
Age
Salary
Vehicle Age
Claim Amount
```

---

Represented as:

```text
X
```

---

# Target Variable

## Theory

The output we want to predict.

---

Example:

```text
Purchased

Fraud

Claim Severity
```

---

Represented as:

```text
y
```

---

# Example

Features:

```text
Age
Salary
```

Target:

```text
Purchased
```

---

Machine Learning:

```text
X → y
```

---

# Training Data

## Theory

Data used to teach the model.

---

Example:

```text
80%
```

of total dataset.

---

# Testing Data

## Theory

Used to evaluate model performance.

---

Example:

```text
20%
```

of total dataset.

---

# Train-Test Split

```text
Dataset
   │
   ├── Training Data (80%)
   │
   └── Testing Data (20%)
```

---

## Python Example

```python
from sklearn.model_selection import train_test_split

X_train,
X_test,
y_train,
y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)
```

---

# Model

## Theory

A mathematical function that learns patterns from data.

---

Example:

```text
Input
  ↓
Model
  ↓
Prediction
```

---

# Training

## Theory

The process where the model learns from training data.

---

Workflow:

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

## Theory

Using a trained model on unseen data.

---

Example:

```text
New Customer
      ↓
Model
      ↓
Prediction
```

---

# Machine Learning Workflow

```text
Collect Data
      ↓
Data Cleaning
      ↓
EDA
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
      ↓
Deployment
```

---

# Classification vs Regression

## Classification

Predict Categories.

---

Examples:

```text
Spam / Not Spam

Fraud / Not Fraud

Claim Approved / Rejected
```

---

Output:

```text
Discrete Values
```

---

# Regression

Predict Continuous Values.

---

Examples:

```text
House Price

Insurance Premium

Claim Amount
```

---

Output:

```text
Numeric Values
```

---

# Example

Classification:

```text
Fraud = Yes
```

---

Regression:

```text
Claim Amount = ₹25,000
```

---

# Overfitting

## Theory

Model memorizes training data.

---

Behavior:

```text
Excellent Training Accuracy

Poor Test Accuracy
```

---

Visualization:

```text
Memorization
```

instead of learning.

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

# Bias vs Variance

## High Bias

```text
Underfitting
```

---

## High Variance

```text
Overfitting
```

---

Goal:

```text
Balance Both
```

---

# Evaluation Metrics

Used to measure model performance.

---

## Classification Metrics

```text
Accuracy
Precision
Recall
F1 Score
ROC-AUC
```

---

## Regression Metrics

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
90 Correct

100 Total
```

Accuracy:

```text
90%
```

---

# Confusion Matrix

## Theory

Shows prediction results.

---

Example:

| | Predicted Yes | Predicted No |
|---|---|---|
| Actual Yes | TP | FN |
| Actual No | FP | TN |

---

Terms:

```text
TP = True Positive

TN = True Negative

FP = False Positive

FN = False Negative
```

---

# Loss Function

## Theory

Measures prediction error.

---

Goal:

```text
Minimize Loss
```

---

Examples:

```text
Mean Squared Error

Cross Entropy Loss
```

---

# Gradient Descent

## Theory

Optimization algorithm used to minimize loss.

---

Workflow:

```text
Prediction
     ↓
Loss
     ↓
Gradient
     ↓
Update Weights
```

---

# Feature Scaling

Why?

Example:

```text
Age = 25

Salary = 500000
```

Different scales can affect learning.

---

Methods:

```text
Standardization

Normalization
```

---

# Machine Learning Libraries

## NumPy

```text
Numerical Computation
```

---

## Pandas

```text
Data Analysis
```

---

## Matplotlib

```text
Visualization
```

---

## Scikit-Learn

```text
Machine Learning Models
```

---

# Simple Machine Learning Example

## Linear Regression

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

## Claim Severity Prediction

Features:

```text
Driver Age
Vehicle Age
Claim Amount
Policy Type
```

Target:

```text
Claim Severity
```

Workflow:

```text
Historical Claims
      ↓
Train Model
      ↓
Predict Severity
```

---

# AI Example

## Customer Churn Prediction

Features:

```text
Age
Usage
Subscription
```

Target:

```text
Leave or Stay
```

---

Machine Learning predicts:

```text
Churn Probability
```

---

# Interview Questions

### Q1. What is Machine Learning?

```text
Machine Learning enables systems to learn patterns from data and make predictions without explicit programming.
```

---

### Q2. What are Features?

```text
Input variables used for prediction.
```

---

### Q3. What is a Target Variable?

```text
The output variable the model predicts.
```

---

### Q4. Difference between Classification and Regression?

```text
Classification:
Predict Categories.

Regression:
Predict Numerical Values.
```

---

### Q5. What is Overfitting?

```text
When a model memorizes training data and performs poorly on unseen data.
```

---

# Learning Path

```text
ML Fundamentals
      ↓
Data
      ↓
Features & Labels
      ↓
Train-Test Split
      ↓
Supervised Learning
      ↓
Unsupervised Learning
      ↓
Regression
      ↓
Classification
      ↓
Model Evaluation
      ↓
Optimization
      ↓
Deployment
```

# Most Important Concepts for AI Engineers

```text
Features
Labels
Training
Testing
Classification
Regression
Overfitting
Underfitting
Evaluation Metrics
Loss Functions
Gradient Descent
```

These concepts form the foundation of:

```text
Machine Learning
Deep Learning
Computer Vision
NLP
Transformers
LLMs
Generative AI
Agentic AI
```

A strong understanding of Machine Learning Fundamentals is essential before learning algorithms such as:

```text
Linear Regression
Logistic Regression
Decision Trees
Random Forest
XGBoost
Neural Networks
Transformers
```