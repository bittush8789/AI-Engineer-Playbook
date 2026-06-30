# Regression in Machine Learning

## What is Regression?

Regression is a type of **Supervised Learning** used to predict **continuous numerical values**.

Unlike Classification:

```text
Classification → Categories

Regression → Numbers
```

---

# Examples of Regression Problems

```text
House Price Prediction

Insurance Premium Prediction

Claim Amount Prediction

Sales Forecasting

Stock Price Prediction

Temperature Prediction
```

---

# Real-World Example

## House Price Prediction

Input Features:

```text
House Size
Bedrooms
Location
Age of House
```

Output:

```text
₹75,00,000
```

Since the output is a number, this is a Regression problem.

---

# Why Regression?

Businesses often need numerical predictions.

Examples:

```text
How much will a claim cost?

What will next month's sales be?

What premium should be charged?

What is the expected loss?
```

---

# How Regression Works

```text
Historical Data
        ↓
Train Model
        ↓
Learn Relationship
        ↓
Predict Future Values
```

---

# Dataset Example

| House Size | Price |
|------------|--------|
| 1000 | 50 Lakh |
| 1500 | 75 Lakh |
| 2000 | 1 Crore |

---

Features (X):

```text
House Size
```

Target (y):

```text
Price
```

---

# Regression Visualization

```text
Price
 ^
 |
 |           *
 |        *
 |     *
 |  *
 +------------------>
       House Size
```

As house size increases:

```text
Price Increases
```

---

# Types of Regression

```text
Linear Regression
Polynomial Regression
Ridge Regression
Lasso Regression
ElasticNet Regression
```

---

# 1. Linear Regression

## Theory

Linear Regression finds the best straight line that represents the relationship between variables.

---

## Equation

```text
y = mx + b
```

Where:

```text
y = Prediction

m = Slope

x = Input Feature

b = Intercept
```

---

## Example

```text
House Size = 1500

Price = ₹75,00,000
```

Model learns:

```text
Bigger House
      ↓
Higher Price
```

---

## Visualization

```text
Price
 ^
 |
 |        *
 |      *
 |    *
 |  *
 +---------------->
     House Size
```

---

## Python Example

```python
from sklearn.linear_model import LinearRegression

model = LinearRegression()

model.fit(
    X_train,
    y_train
)

predictions = model.predict(
    X_test
)
```

---

# Multiple Linear Regression

## Theory

Uses multiple features.

---

Example:

```text
Price

=

House Size
+
Bedrooms
+
Location
+
Age
```

---

Dataset

| Size | Bedrooms | Price |
|--------|----------|--------|
| 1000 | 2 | 50L |
| 1500 | 3 | 75L |

---

# 2. Polynomial Regression

## Theory

Used when data is not linear.

---

Example:

```text
Sales Growth
Population Growth
```

---

Visualization

```text
     *
   *
 *
   *
      *
```

Curved relationship.

---

# 3. Ridge Regression

## Theory

Linear Regression + Regularization.

---

Purpose:

```text
Reduce Overfitting
```

---

Adds penalty to large coefficients.

---

Benefits:

```text
Better Generalization
```

---

# 4. Lasso Regression

## Theory

Can eliminate unnecessary features.

---

Benefits:

```text
Feature Selection
Reduce Overfitting
```

---

# 5. ElasticNet

## Theory

Combination of:

```text
Ridge
+
Lasso
```

---

Used when:

```text
Many Features
High Correlation
```

---

# Assumptions of Linear Regression

## 1. Linear Relationship

```text
Input and Output should have a linear relationship.
```

---

## 2. Independence

Observations should be independent.

---

## 3. No Multicollinearity

Features should not be highly correlated.

---

## 4. Homoscedasticity

Error variance should remain constant.

---

## 5. Normal Residuals

Errors should be normally distributed.

---

# Loss Function in Regression

Most common:

```text
Mean Squared Error (MSE)
```

---

Formula:

```text
(actual - predicted)^2
```

---

Example

Actual:

```text
100
```

Prediction:

```text
90
```

---

Error:

```text
10
```

---

Loss:

```text
10² = 100
```

---

# Evaluation Metrics

## 1. MAE

Mean Absolute Error

---

Formula:

```text
Average Absolute Error
```

---

Example:

```text
Actual = 100

Prediction = 90

Error = 10
```

---

# 2. MSE

Mean Squared Error

---

Formula:

```text
Average Squared Error
```

---

Benefits:

```text
Penalizes Large Errors
```

---

# 3. RMSE

Root Mean Squared Error

---

Formula:

```text
√MSE
```

---

Benefits:

```text
Same Unit as Target
```

---

# 4. R² Score

## Theory

Measures how well the model explains data.

---

Range:

```text
0 to 1
```

---

Interpretation:

```text
1 = Perfect Prediction

0 = Poor Prediction
```

---

# Overfitting in Regression

## Theory

Model memorizes training data.

---

Behavior:

```text
Excellent Training Performance

Poor Test Performance
```

---

# Underfitting in Regression

## Theory

Model fails to learn patterns.

---

Behavior:

```text
Poor Training Performance

Poor Testing Performance
```

---

# Good Fit

```text
Good Training Performance

Good Testing Performance
```

---

# Regression Workflow

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
Train Regression Model
      ↓
Evaluate
      ↓
Deploy
```

---

# Insurance Example

## Claim Amount Prediction

Features:

```text
Vehicle Age
Driver Age
Accident Type
Coverage Type
```

---

Target:

```text
Claim Amount
```

Output:

```text
₹25,000
```

---

Regression Model Predicts:

```text
Expected Claim Cost
```

---

# Insurance Example 2

## Premium Prediction

Features:

```text
Age
Location
Driving History
Vehicle Type
```

---

Target:

```text
Insurance Premium
```

Output:

```text
₹15,500
```

---

# Business Applications

```text
Sales Forecasting
Revenue Prediction
Demand Forecasting
Risk Modeling
Premium Prediction
Claim Severity Prediction
Financial Forecasting
```

---

# Complete Scikit-Learn Example

```python
from sklearn.linear_model import LinearRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)

model = LinearRegression()

model.fit(
    X_train,
    y_train
)

predictions = model.predict(
    X_test
)

mse = mean_squared_error(
    y_test,
    predictions
)

print(mse)
```

---

# Interview Questions

### Q1. What is Regression?

```text
A supervised learning technique used to predict continuous numerical values.
```

---

### Q2. Give examples of Regression problems.

```text
House Price Prediction
Claim Amount Prediction
Sales Forecasting
Premium Prediction
```

---

### Q3. What is Linear Regression?

```text
A regression algorithm that models a linear relationship between input and output variables.
```

---

### Q4. What is R² Score?

```text
A metric that measures how well the model explains variance in the data.
```

---

### Q5. Difference between Regression and Classification?

```text
Regression:
Predicts Numbers

Classification:
Predicts Categories
```

---

# Learning Path

```text
Regression Basics
      ↓
Linear Regression
      ↓
Multiple Linear Regression
      ↓
Polynomial Regression
      ↓
Loss Functions
      ↓
Evaluation Metrics
      ↓
Regularization
      ↓
Ridge Regression
      ↓
Lasso Regression
      ↓
Real-World Projects
```

# Most Important Topics for AI Engineers

```text
Linear Regression
Multiple Regression
Polynomial Regression
MSE
RMSE
MAE
R² Score
Overfitting
Regularization
Ridge Regression
Lasso Regression
```

Regression is one of the most widely used Machine Learning techniques in:

```text
Insurance Analytics
Finance
Forecasting
Healthcare
Supply Chain
Retail
Predictive Analytics
AI Engineering
```

It serves as the foundation for understanding advanced Machine Learning and Deep Learning algorithms.