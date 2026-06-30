# Classification in Machine Learning

## What is Classification?

Classification is a type of **Supervised Learning** where the goal is to predict **categories (classes)** instead of numerical values.

---

## Basic Idea

```text
Input Features
      ↓
Machine Learning Model
      ↓
Predicted Class
```

---

## Examples

```text
Spam / Not Spam

Fraud / Not Fraud

Claim Approved / Rejected

Disease / No Disease

Customer Churn / No Churn
```

---

# Why Classification?

Businesses often need categorical decisions.

Examples:

```text
Is this claim fraudulent?

Will the customer churn?

Is this email spam?

Should this loan be approved?
```

---

# Regression vs Classification

| Regression | Classification |
|------------|---------------|
| Predicts Numbers | Predicts Categories |
| House Price | Spam Detection |
| Claim Amount | Fraud Detection |
| Sales Forecast | Customer Churn |

---

## Example

Regression:

```text
Claim Amount = ₹25,000
```

Classification:

```text
Fraud = Yes
```

---

# Classification Workflow

```text
Historical Data
      ↓
Train Model
      ↓
Learn Patterns
      ↓
Predict Class
```

---

# Dataset Example

## Loan Approval

| Age | Salary | Approved |
|------|---------|-----------|
| 25 | 50000 | Yes |
| 30 | 70000 | No |
| 35 | 90000 | Yes |

---

Features (X):

```text
Age
Salary
```

Target (y):

```text
Approved
```

---

# Types of Classification

```text
Binary Classification
Multi-Class Classification
Multi-Label Classification
```

---

# 1. Binary Classification

## Theory

Two possible classes.

---

Examples:

```text
Yes / No

True / False

0 / 1

Fraud / Not Fraud
```

---

## Example

Insurance Fraud Detection

Input:

```text
Claim Details
```

Output:

```text
Fraud
```

or

```text
Not Fraud
```

---

# 2. Multi-Class Classification

## Theory

More than two classes.

---

Examples:

```text
Low Risk

Medium Risk

High Risk
```

---

Example:

Animal Classification

```text
Cat

Dog

Bird
```

---

# 3. Multi-Label Classification

## Theory

One record can belong to multiple classes.

---

Example:

Movie Genres

```text
Action
Comedy
Drama
```

A movie can belong to all three.

---

# How Classification Works

Suppose:

```text
Age = 30

Salary = 70000
```

Model learns patterns from historical data.

---

Prediction:

```text
Loan Approved
```

---

# Probability-Based Classification

Most classifiers predict probabilities.

---

Example:

```text
Fraud Probability

0.95
```

Meaning:

```text
95% Chance Fraud
```

---

Decision:

```text
Probability > 0.5

Fraud
```

---

# Popular Classification Algorithms

```text
Logistic Regression
Decision Tree
Random Forest
XGBoost
LightGBM
CatBoost
SVM
KNN
Naive Bayes
```

---

# 1. Logistic Regression

## Theory

Most common classification algorithm.

---

Despite the name:

```text
It is used for Classification
```

not Regression.

---

Output:

```text
Probability
```

Range:

```text
0 to 1
```

---

## Example

```text
0.90 → Fraud

0.10 → Not Fraud
```

---

## Python Example

```python
from sklearn.linear_model import LogisticRegression

model = LogisticRegression()

model.fit(
    X_train,
    y_train
)

predictions = model.predict(
    X_test
)
```

---

# 2. Decision Tree

## Theory

Uses decision rules.

---

Visualization:

```text
Claim Amount > 50000?
          |
     Yes / No
```

---

Output:

```text
Fraud
Not Fraud
```

---

Advantages:

```text
Easy to Interpret
```

---

# 3. Random Forest

## Theory

Collection of multiple Decision Trees.

---

Visualization:

```text
Tree 1

Tree 2

Tree 3

Tree 4
```

---

Final Prediction:

```text
Voting
```

---

Advantages:

```text
High Accuracy
Less Overfitting
```

---

# 4. XGBoost

## Theory

Advanced boosting algorithm.

---

Benefits:

```text
Very High Accuracy
Fast Training
Industry Favorite
```

---

Applications:

```text
Fraud Detection
Risk Scoring
Credit Modeling
```

---

# Classification Metrics

Classification models require evaluation.

---

# Confusion Matrix

| | Predicted Yes | Predicted No |
|---|---|---|
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

# Accuracy

## Formula

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

# Precision

## Theory

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

Example:

Fraud Detection

```text
Predicted Fraud = 100

Actually Fraud = 80
```

Precision:

```text
80%
```

---

# Recall

## Theory

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

Example:

Actual Fraud Cases:

```text
100
```

Detected:

```text
90
```

Recall:

```text
90%
```

---

# F1 Score

## Theory

Balance between:

```text
Precision
Recall
```

---

Useful for:

```text
Imbalanced Datasets
```

---

# ROC-AUC

## Theory

Measures model discrimination ability.

---

Range:

```text
0.5 → Random

1.0 → Perfect
```

---

# Class Imbalance

## Theory

Occurs when one class dominates.

---

Example:

```text
9900 Normal Claims

100 Fraud Claims
```

---

Problem:

```text
Accuracy Can Mislead
```

---

Model predicts:

```text
Always Normal
```

Accuracy:

```text
99%
```

but detects no fraud.

---

Use:

```text
Precision
Recall
F1 Score
```

instead.

---

# Overfitting

## Theory

Model memorizes training data.

---

Behavior:

```text
High Training Accuracy

Low Testing Accuracy
```

---

# Underfitting

## Theory

Model fails to learn patterns.

---

Behavior:

```text
Low Training Accuracy

Low Testing Accuracy
```

---

# Classification Workflow

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
Train Classifier
      ↓
Evaluate
      ↓
Deploy
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
Historical Claims
      ↓
Train Model
      ↓
Learn Fraud Patterns
      ↓
Predict Fraud
```

---

# Insurance Example 2

## Claim Routing

Features:

```text
Claim Amount
Claim Type
Accident Type
```

Target:

```text
Low Severity

Medium Severity

High Severity
```

---

Output:

```text
Claim Queue Assignment
```

---

# Banking Example

Input:

```text
Income
Credit Score
Loan History
```

Output:

```text
Loan Approved

Loan Rejected
```

---

# Complete Scikit-Learn Example

```python
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import train_test_split
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

# Interview Questions

### Q1. What is Classification?

```text
A supervised learning technique used to predict categories or classes.
```

---

### Q2. Difference between Classification and Regression?

```text
Classification:
Predict Categories

Regression:
Predict Numbers
```

---

### Q3. What is a Confusion Matrix?

```text
A table used to evaluate classification models.
```

---

### Q4. Why is Accuracy not always sufficient?

```text
Because it can be misleading for imbalanced datasets.
```

---

### Q5. What is Precision?

```text
The percentage of predicted positives that are actually positive.
```

---

# Learning Path

```text
Classification Basics
        ↓
Binary Classification
        ↓
Multi-Class Classification
        ↓
Logistic Regression
        ↓
Decision Trees
        ↓
Random Forest
        ↓
XGBoost
        ↓
Confusion Matrix
        ↓
Precision & Recall
        ↓
Model Evaluation
```

# Most Important Topics for AI Engineers

```text
Binary Classification
Multi-Class Classification
Logistic Regression
Decision Trees
Random Forest
XGBoost
Confusion Matrix
Accuracy
Precision
Recall
F1 Score
ROC-AUC
```

Classification is one of the most widely used Machine Learning techniques in:

```text
Fraud Detection
Insurance Claims
Credit Scoring
Cyber Security
Medical Diagnosis
Customer Churn Prediction
Spam Detection
Recommendation Systems
```

It forms the foundation for many real-world AI systems that make business decisions and automate operational workflows.