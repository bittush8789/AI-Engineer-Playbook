# Feature Engineering & Exploratory Data Analysis (EDA)

## What is Feature Engineering?

Feature Engineering is the process of creating, transforming, selecting, and improving features (input variables) to help Machine Learning models learn better patterns.

---

## Why Feature Engineering?

Machine Learning models learn from features.

```text
Better Features
      ↓
Better Patterns
      ↓
Better Predictions
```

Even a simple model with good features can outperform a complex model with poor features.

---

# Example

Raw Data:

| Date of Birth |
|---------------|
| 1998-05-10 |

---

Feature Engineering:

```text
Date of Birth
      ↓
Age
```

Result:

| Age |
|------|
| 27 |

Age is more useful than Date of Birth for many ML models.

---

# Types of Feature Engineering

```text
Feature Creation
Feature Transformation
Feature Encoding
Feature Scaling
Feature Extraction
Feature Selection
```

---

# 1. Feature Creation

## Theory

Create new features from existing data.

---

## Example

Dataset:

| Salary |
|----------|
| 50000 |

Create Bonus:

```python
df["Bonus"] = (
    df["Salary"] * 0.1
)
```

---

Result:

| Salary | Bonus |
|----------|---------|
| 50000 | 5000 |

---

# Date Features

## Example

```python
df["Date"] = pd.to_datetime(
    df["Date"]
)

df["Year"] = df["Date"].dt.year

df["Month"] = df["Date"].dt.month

df["Day"] = df["Date"].dt.day
```

---

# Insurance Example

Claim Date:

```text
2025-05-10
```

Create:

```text
Month
Quarter
DayOfWeek
```

---

# 2. Feature Transformation

## Log Transformation

Used for skewed data.

---

Before:

```text
100
500
1000
500000
```

---

After:

```python
import numpy as np

df["Salary"] = np.log(
    df["Salary"]
)
```

---

Benefits:

```text
Reduce Skewness
Improve Model Performance
```

---

# Square Root Transformation

```python
df["Value"] = np.sqrt(
    df["Value"]
)
```

---

# 3. Encoding Categorical Features

Machine Learning requires numerical input.

---

Example:

```text
Male
Female
```

---

# Label Encoding

```python
from sklearn.preprocessing import LabelEncoder

le = LabelEncoder()

df["Gender"] = le.fit_transform(
    df["Gender"]
)
```

---

Output:

```text
Male = 1

Female = 0
```

---

# One-Hot Encoding

```python
pd.get_dummies(
    df,
    columns=["Gender"]
)
```

---

Output:

```text
Gender_Male

Gender_Female
```

---

# 4. Feature Scaling

## Why Scaling?

Features often have different ranges.

---

Example:

```text
Age = 25

Salary = 500000
```

---

Scaling ensures equal importance.

---

# Standardization

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()

df[["Salary"]] = scaler.fit_transform(
    df[["Salary"]]
)
```

---

# Normalization

```python
from sklearn.preprocessing import MinMaxScaler

scaler = MinMaxScaler()

df[["Salary"]] = scaler.fit_transform(
    df[["Salary"]]
)
```

---

# 5. Feature Selection

## Theory

Select only important features.

---

Benefits:

```text
Faster Training
Reduced Overfitting
Better Interpretability
```

---

Example:

```text
Age
Salary
Credit Score
```

Useful.

---

Remove:

```text
Customer ID
Random Numbers
```

---

# Correlation-Based Selection

```python
df.corr()
```

---

Features with strong relationship to target are preferred.

---

# 6. Feature Extraction

## Theory

Reduce dimensionality while preserving information.

---

Examples:

```text
PCA
SVD
Autoencoders
```

---

# PCA Example

```python
from sklearn.decomposition import PCA

pca = PCA(
    n_components=2
)

X_new = pca.fit_transform(X)
```

---

Benefits:

```text
Reduce Features
Improve Speed
Reduce Noise
```

---

# Real AI Examples

## Insurance

Raw Data:

```text
Claim Date
Claim Amount
Vehicle Age
```

---

Engineered Features:

```text
Claim Month
Claim Quarter
Claim Category
```

---

## E-commerce

Raw:

```text
Purchase Date
```

Create:

```text
Weekend Purchase
Month
Holiday Flag
```

---

# What is EDA?

EDA stands for:

```text
Exploratory Data Analysis
```

EDA is the process of understanding and investigating data before building models.

---

# Why EDA?

EDA helps answer:

```text
What does the data look like?

Are there missing values?

Are there outliers?

Which features are important?

Are there patterns?
```

---

# EDA Workflow

```text
Load Data
     ↓
Understand Structure
     ↓
Summary Statistics
     ↓
Missing Values
     ↓
Outlier Analysis
     ↓
Distribution Analysis
     ↓
Correlation Analysis
     ↓
Visualization
```

---

# Step 1: Load Dataset

```python
import pandas as pd

df = pd.read_csv(
    "data.csv"
)
```

---

# Step 2: View Data

## head()

```python
df.head()
```

---

## tail()

```python
df.tail()
```

---

## shape

```python
df.shape
```

Output:

```text
(rows, columns)
```

---

# Step 3: Dataset Information

```python
df.info()
```

Shows:

```text
Columns
Data Types
Missing Values
```

---

# Step 4: Summary Statistics

```python
df.describe()
```

Shows:

```text
Mean
Median
Std
Min
Max
Percentiles
```

---

# Step 5: Missing Values

```python
df.isnull().sum()
```

---

# Step 6: Duplicate Records

```python
df.duplicated().sum()
```

---

# Step 7: Distribution Analysis

## Histogram

```python
import matplotlib.pyplot as plt

df["Salary"].hist()

plt.show()
```

---

Purpose:

```text
Understand Distribution
Detect Skewness
```

---

# Step 8: Outlier Analysis

## Box Plot

```python
import seaborn as sns

sns.boxplot(
    x=df["Salary"]
)
```

---

Purpose:

```text
Detect Outliers
```

---

# Step 9: Correlation Analysis

```python
df.corr()
```

---

# Heatmap

```python
sns.heatmap(
    df.corr(),
    annot=True
)
```

---

Example Correlation Strength

```text
+1  Strong Positive

0   No Relation

-1  Strong Negative
```

---

# Step 10: Relationship Analysis

## Scatter Plot

```python
plt.scatter(
    df["Age"],
    df["Salary"]
)

plt.show()
```

---

Purpose:

```text
Identify Relationships
```

---

# EDA Example

Insurance Claims Dataset

| ClaimAmount | Fraud |
|-------------|--------|
| 5000 | 0 |
| 10000 | 0 |
| 25000 | 1 |

---

Questions:

```text
Average Claim Amount?

Fraud Rate?

Outliers?

Claim Distribution?
```

EDA answers these questions.

---

# EDA in Machine Learning

Before Training:

```text
EDA
 ↓
Feature Engineering
 ↓
Feature Selection
 ↓
Model Training
```

---

# Complete ML Workflow

```text
Collect Data
      ↓
Data Cleaning
      ↓
EDA
      ↓
Feature Engineering
      ↓
Feature Selection
      ↓
Train/Test Split
      ↓
Model Training
      ↓
Evaluation
```

---

# Interview Questions

### Q1. What is Feature Engineering?

```text
The process of creating and transforming features to improve model performance.
```

---

### Q2. Why is Feature Engineering important?

```text
Good features improve model accuracy and learning.
```

---

### Q3. What is EDA?

```text
Exploratory Data Analysis is the process of understanding and analyzing data before modeling.
```

---

### Q4. What tools are commonly used for EDA?

```text
Pandas
Matplotlib
Seaborn
Plotly
```

---

### Q5. What is PCA?

```text
A dimensionality reduction technique used for feature extraction.
```

---

# Learning Path

```text
Feature Creation
      ↓
Encoding
      ↓
Scaling
      ↓
Feature Selection
      ↓
Feature Extraction
      ↓
EDA Basics
      ↓
Statistics
      ↓
Visualization
      ↓
Correlation Analysis
      ↓
Machine Learning
```

# Most Important Topics for AI Engineers

```text
Feature Creation
Encoding
Scaling
Feature Selection
PCA
EDA
Histograms
Box Plots
Scatter Plots
Heatmaps
Correlation Analysis
```

These concepts are heavily used in:

```text
Machine Learning
Deep Learning
Predictive Analytics
Fraud Detection
Recommendation Systems
MLOps
LLMOps
Generative AI
```

A common industry rule is:

```text
Better Features
      >
Better Algorithms
```

Many real-world ML performance gains come from strong Feature Engineering and thorough EDA rather than changing the model itself.