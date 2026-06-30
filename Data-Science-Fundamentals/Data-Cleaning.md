# Data Cleaning for AI & Machine Learning

## What is Data Cleaning?

Data Cleaning is the process of identifying and fixing errors, inconsistencies, and missing values in raw data.

Raw data is usually:

```text
Incomplete
Incorrect
Duplicate
Inconsistent
Noisy
```

Data Cleaning converts raw data into high-quality data suitable for analysis and machine learning.

---

# Why Data Cleaning is Important?

Machine Learning models learn from data.

If data quality is poor:

```text
Poor Data
     ↓
Poor Model
```

This is known as:

```text
Garbage In
Garbage Out (GIGO)
```

---

# Real-World Example

Raw Customer Data

| Name | Age | Salary |
|--------|--------|--------|
| Bittu | 25 | 50000 |
| Rahul | NULL | 60000 |
| Rahul | NULL | 60000 |
| Amit | 200 | 70000 |

Problems:

```text
Missing Values
Duplicate Records
Invalid Age
```

---

# Data Cleaning Workflow

```text
Load Data
    ↓
Understand Data
    ↓
Find Missing Values
    ↓
Handle Duplicates
    ↓
Fix Data Types
    ↓
Handle Outliers
    ↓
Validate Data
    ↓
Save Clean Data
```

---

# Step 1: Load Dataset

## Example

```python
import pandas as pd

df = pd.read_csv(
    "employees.csv"
)

print(df.head())
```

---

# Step 2: Understand Data

## View Data

```python
df.head()
```

Shows:

```text
First 5 Rows
```

---

## Dataset Information

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

## Statistical Summary

```python
df.describe()
```

Shows:

```text
Mean
Min
Max
Std
Percentiles
```

---

# Step 3: Handle Missing Values

## What are Missing Values?

Missing values occur when data is unavailable.

Example:

```text
Name Age

Bittu 25

Rahul NaN
```

---

# Detect Missing Values

```python
df.isnull()
```

---

# Count Missing Values

```python
df.isnull().sum()
```

Output:

```text
Age 1
Salary 0
```

---

# Fill Missing Values

## Fill with Constant

```python
df.fillna(0)
```

---

## Fill with Mean

```python
df["Age"] = df[
    "Age"
].fillna(
    df["Age"].mean()
)
```

---

## Fill with Median

```python
df["Age"] = df[
    "Age"
].fillna(
    df["Age"].median()
)
```

---

# Why Median?

For skewed data:

```text
Median is more robust than Mean.
```

---

# Remove Missing Rows

```python
df.dropna()
```

---

# Remove Missing Columns

```python
df.dropna(
    axis=1
)
```

---

# Step 4: Remove Duplicates

## What are Duplicates?

Repeated records.

---

Example:

```text
Bittu 25

Bittu 25
```

---

# Detect Duplicates

```python
df.duplicated()
```

---

# Count Duplicates

```python
df.duplicated().sum()
```

---

# Remove Duplicates

```python
df.drop_duplicates()
```

---

# Step 5: Fix Data Types

## Example

Age stored as string.

---

```python
print(
    df["Age"].dtype
)
```

Output:

```text
object
```

---

# Convert to Integer

```python
df["Age"] = df[
    "Age"
].astype(int)
```

---

# Convert Date

```python
df["Date"] = pd.to_datetime(
    df["Date"]
)
```

---

# Step 6: Handle Invalid Data

## Example

Age:

```text
25
30
200
```

Age 200 is invalid.

---

# Detect Invalid Values

```python
df[
    df["Age"] > 100
]
```

---

# Remove Invalid Rows

```python
df = df[
    df["Age"] <= 100
]
```

---

# Step 7: Handle Outliers

## What is an Outlier?

An unusually large or small value.

---

Example:

```text
1000
1200
1100
150000
```

150000 is an outlier.

---

# Why Outliers Matter?

They can:

```text
Distort Mean
Reduce Accuracy
Mislead Models
```

---

# Detect Using IQR

## Formula

```text
IQR

=

Q3 - Q1
```

---

## Example

```python
Q1 = df[
    "Salary"
].quantile(0.25)

Q3 = df[
    "Salary"
].quantile(0.75)

IQR = Q3 - Q1
```

---

# Outlier Boundaries

```python
lower = Q1 - 1.5 * IQR

upper = Q3 + 1.5 * IQR
```

---

# Remove Outliers

```python
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

# Step 8: String Cleaning

## Remove Spaces

```python
df["Name"] = df[
    "Name"
].str.strip()
```

---

# Convert to Lowercase

```python
df["City"] = df[
    "City"
].str.lower()
```

---

# Convert to Uppercase

```python
df["State"] = df[
    "State"
].str.upper()
```

---

# Replace Values

```python
df["Gender"] = df[
    "Gender"
].replace(
    {
        "M":"Male",
        "F":"Female"
    }
)
```

---

# Step 9: Handle Categorical Values

Example:

```text
Male
Female
```

Machine Learning requires numbers.

---

# Label Encoding

```python
from sklearn.preprocessing import LabelEncoder

le = LabelEncoder()

df["Gender"] = le.fit_transform(
    df["Gender"]
)
```

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

# Step 10: Feature Scaling

## Why Scaling?

Different ranges cause model issues.

---

Example:

```text
Age = 25

Salary = 500000
```

---

# Standardization

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()

df[
    ["Salary"]
] = scaler.fit_transform(
    df[
        ["Salary"]
    ]
)
```

---

# Normalization

```python
from sklearn.preprocessing import MinMaxScaler

scaler = MinMaxScaler()

df[
    ["Salary"]
] = scaler.fit_transform(
    df[
        ["Salary"]
    ]
)
```

---

# Data Validation

## Check Data Types

```python
df.dtypes
```

---

## Check Missing Values

```python
df.isnull().sum()
```

---

## Check Duplicates

```python
df.duplicated().sum()
```

---

# Complete Data Cleaning Example

```python
import pandas as pd

df = pd.read_csv(
    "employees.csv"
)

df.drop_duplicates(
    inplace=True
)

df["Age"] = df[
    "Age"
].fillna(
    df["Age"].median()
)

df["Name"] = df[
    "Name"
].str.strip()

print(df.head())
```

---

# Data Cleaning in Machine Learning

Workflow:

```text
Raw Data
     ↓
Data Cleaning
     ↓
Feature Engineering
     ↓
EDA
     ↓
Train/Test Split
     ↓
Model Training
```

---

# Insurance Example

Claims Dataset

```text
ClaimID Amount

101 5000

102 NULL

102 NULL

103 2500000
```

Problems:

```text
Missing Values
Duplicates
Outliers
```

---

Cleaning:

```text
Fill Missing Values
Remove Duplicates
Handle Outliers
```

---

Result:

```text
Reliable Dataset
```

---

# AI Example

Customer Churn Dataset

Features:

```text
Age
Income
Gender
Location
```

Before Training:

```text
Handle Missing Data
Encode Categories
Scale Features
```

---

# Common Data Cleaning Techniques

| Problem | Solution |
|----------|----------|
| Missing Values | fillna(), dropna() |
| Duplicates | drop_duplicates() |
| Outliers | IQR, Z-Score |
| Wrong Data Type | astype() |
| Invalid Values | Filtering |
| Extra Spaces | strip() |
| Categories | Encoding |
| Different Scales | Standardization |

---

# Interview Questions

### Q1. What is Data Cleaning?

```text
The process of detecting and correcting inaccurate or incomplete data.
```

---

### Q2. Why is Data Cleaning important?

```text
Poor quality data leads to poor machine learning models.
```

---

### Q3. How do you handle missing values?

```text
fillna()

dropna()
```

---

### Q4. What is an Outlier?

```text
An unusually large or small value.
```

---

### Q5. How do you remove duplicates?

```python
df.drop_duplicates()
```

---

# Learning Path

```text
Load Dataset
      ↓
Understand Data
      ↓
Missing Values
      ↓
Duplicates
      ↓
Data Types
      ↓
Outliers
      ↓
String Cleaning
      ↓
Encoding
      ↓
Scaling
      ↓
Validation
```

# Most Important Data Cleaning Topics for AI Engineers

```text
Missing Values
Duplicates
Outliers
Data Types
String Cleaning
Encoding
Scaling
Validation
```

Data Cleaning is one of the most critical steps in:

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

In real-world projects, data cleaning often consumes **60–80% of the total project effort**, making it one of the highest-value skills for AI Engineers.