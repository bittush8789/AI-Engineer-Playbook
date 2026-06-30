# Data Preprocessing & Data Visualization

## What is Data Preprocessing?

Data Preprocessing is the process of transforming raw data into a clean, structured, and machine-learning-ready format.

Raw Data:

```text
Incomplete
Noisy
Inconsistent
Unstructured
```

Processed Data:

```text
Clean
Accurate
Consistent
Ready for Modeling
```

---

# Why Data Preprocessing?

Machine Learning models cannot directly work with raw data.

Example:

| Name | Age | Salary | Gender |
|--------|--------|--------|--------|
| Bittu | 25 | 50000 | Male |
| Rahul | NaN | 60000 | Female |

Problems:

```text
Missing Values
Categorical Data
Different Scales
```

Must be processed before training.

---

# Data Preprocessing Workflow

```text
Collect Data
      ↓
Data Cleaning
      ↓
Handle Missing Values
      ↓
Handle Outliers
      ↓
Encoding
      ↓
Feature Scaling
      ↓
Feature Engineering
      ↓
Train/Test Split
      ↓
Model Training
```

---

# 1. Handling Missing Values

## Theory

Missing values occur when information is unavailable.

Example:

```text
Age = NaN
```

---

## Detect Missing Values

```python
import pandas as pd

df.isnull().sum()
```

---

## Fill Missing Values

### Mean

```python
df["Age"] = df["Age"].fillna(
    df["Age"].mean()
)
```

---

### Median

```python
df["Age"] = df["Age"].fillna(
    df["Age"].median()
)
```

---

### Constant

```python
df.fillna(0)
```

---

# 2. Handling Categorical Data

## Theory

Machine Learning models require numerical data.

---

Example:

```text
Male
Female
```

Need conversion.

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

# When to Use?

| Technique | Use Case |
|------------|------------|
| Label Encoding | Ordinal Data |
| One-Hot Encoding | Nominal Data |

---

# 3. Feature Scaling

## Theory

Features often have different ranges.

Example:

```text
Age = 25

Salary = 500000
```

Salary dominates calculations.

---

# Standardization

## Formula

```text
(x - Mean)
/ Std Dev
```

---

## Example

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()

df[["Salary"]] = scaler.fit_transform(
    df[["Salary"]]
)
```

---

# Normalization

## Formula

```text
(x - Min)
/
(Max - Min)
```

Range:

```text
0 to 1
```

---

## Example

```python
from sklearn.preprocessing import MinMaxScaler

scaler = MinMaxScaler()

df[["Salary"]] = scaler.fit_transform(
    df[["Salary"]]
)
```

---

# Standardization vs Normalization

| Standardization | Normalization |
|---------------|---------------|
| Mean = 0 | Range = 0–1 |
| Std = 1 | Fixed Scale |
| Most Common | Neural Networks |

---

# 4. Handling Outliers

## Theory

Outliers are extreme values.

---

Example:

```text
1000
1200
1300
150000
```

---

# Detect Using IQR

```python
Q1 = df["Salary"].quantile(0.25)

Q3 = df["Salary"].quantile(0.75)

IQR = Q3 - Q1
```

---

## Remove Outliers

```python
lower = Q1 - 1.5 * IQR

upper = Q3 + 1.5 * IQR

df = df[
    (
        df["Salary"] >= lower
    )
    &
    (
        df["Salary"] <= upper
    )
]
```

---

# 5. Feature Engineering

## Theory

Creating new features from existing data.

---

Example:

```text
Date of Birth
```

Create:

```text
Age
```

---

## Example

```python
df["Bonus"] = (
    df["Salary"] * 0.1
)
```

---

# 6. Train-Test Split

## Theory

Separate data into:

```text
Training Data
Testing Data
```

---

Typical Split:

```text
80% Training

20% Testing
```

---

## Example

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

# Data Visualization

## What is Data Visualization?

Data Visualization is the graphical representation of data.

Purpose:

```text
Understand Data
Find Patterns
Detect Outliers
Identify Trends
```

---

# Why Visualization?

Before training models:

```text
Understand Data First
```

Visualization helps reveal:

```text
Relationships
Patterns
Anomalies
Distributions
```

---

# Visualization Libraries

## Matplotlib

```python
import matplotlib.pyplot as plt
```

---

## Seaborn

```python
import seaborn as sns
```

---

## Plotly

```python
import plotly.express as px
```

---

# Common Charts

```text
Line Chart
Bar Chart
Histogram
Box Plot
Scatter Plot
Heatmap
Pie Chart
```

---

# 1. Line Chart

## Theory

Used for trends over time.

---

## Example

```python
import matplotlib.pyplot as plt

months = [
    "Jan",
    "Feb",
    "Mar"
]

sales = [
    100,
    150,
    200
]

plt.plot(
    months,
    sales
)

plt.show()
```

---

Example Trend:


::contentReference[oaicite:0]{index=0}


---

# 2. Bar Chart

## Theory

Used for category comparison.

---

## Example

```python
plt.bar(
    ["A","B","C"],
    [10,20,30]
)

plt.show()
```

---

# 3. Histogram

## Theory

Shows data distribution.

---

## Example

```python
plt.hist(
    df["Salary"],
    bins=10
)

plt.show()
```

---

Uses:

```text
Distribution Analysis
Outlier Detection
```

---

# 4. Scatter Plot

## Theory

Shows relationship between variables.

---

## Example

```python
plt.scatter(
    df["Age"],
    df["Salary"]
)

plt.show()
```

---

Example Relationship:


::contentReference[oaicite:1]{index=1}


---

# 5. Box Plot

## Theory

Used to identify:

```text
Outliers
Median
Quartiles
```

---

## Example

```python
sns.boxplot(
    x=df["Salary"]
)
```

---

# 6. Heatmap

## Theory

Visualizes correlation matrix.

---

## Example

```python
import seaborn as sns

sns.heatmap(
    df.corr(),
    annot=True
)
```

---

# Correlation

Range:

```text
-1 to +1
```

---

Interpretation:

```text
+1 → Strong Positive

0 → No Relation

-1 → Strong Negative
```

---

# EDA (Exploratory Data Analysis)

Before Model Training:

```text
Understand Data
```

Steps:

```text
Data Cleaning
Visualization
Statistics
Correlation Analysis
```

---

# Machine Learning Workflow

```text
Raw Data
     ↓
Data Cleaning
     ↓
Data Preprocessing
     ↓
Visualization
     ↓
Feature Engineering
     ↓
Train/Test Split
     ↓
Model Training
     ↓
Evaluation
```

---

# Insurance Example

Claims Dataset

| ClaimAmount | Fraud |
|-------------|--------|
| 5000 | 0 |
| 10000 | 0 |
| 25000 | 1 |

---

Preprocessing:

```text
Handle Missing Values
Encode Categories
Scale Data
```

---

Visualization:

```text
Claim Distribution
Fraud Rate
Correlation Analysis
```

---

# AI Example

Customer Churn Prediction

Features:

```text
Age
Income
Gender
Location
```

Preprocessing:

```text
Encoding
Scaling
Cleaning
```

Visualization:

```text
Histograms
Heatmaps
Scatter Plots
```

---

# Interview Questions

### Q1. What is Data Preprocessing?

```text
The process of transforming raw data into machine-learning-ready data.
```

---

### Q2. Why is Feature Scaling needed?

```text
To bring features to a common scale.
```

---

### Q3. Difference between Standardization and Normalization?

```text
Standardization:
Mean = 0, Std = 1

Normalization:
Range = 0 to 1
```

---

### Q4. What is One-Hot Encoding?

```text
Converting categorical values into binary columns.
```

---

### Q5. Why is Data Visualization important?

```text
It helps identify patterns, trends, and anomalies before model training.
```

---

# Learning Path

```text
Data Cleaning
      ↓
Missing Values
      ↓
Encoding
      ↓
Feature Scaling
      ↓
Outlier Handling
      ↓
Feature Engineering
      ↓
Train-Test Split
      ↓
Matplotlib
      ↓
Seaborn
      ↓
EDA
      ↓
Machine Learning
```

# Most Important Topics for AI Engineers

```text
Missing Values
Encoding
Feature Scaling
Outlier Handling
Feature Engineering
Train-Test Split
Histograms
Scatter Plots
Heatmaps
Correlation Analysis
EDA
```

These concepts are essential for:

```text
Data Science
Machine Learning
Deep Learning
MLOps
LLMOps
Predictive Analytics
Fraud Detection
Generative AI
```

In real-world AI projects, strong preprocessing and visualization skills often have a bigger impact on model performance than trying more complex algorithms.