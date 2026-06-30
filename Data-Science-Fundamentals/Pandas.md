# Pandas for AI & Machine Learning

## What is Pandas?

Pandas is the most popular Python library for:

- Data Analysis
- Data Manipulation
- Data Cleaning
- Data Transformation
- Data Exploration

Pandas is built on top of NumPy and provides powerful data structures for handling tabular data.

---

# Why Pandas?

Real-world data is messy.

Examples:

```text
Missing Values
Duplicate Records
Wrong Data Types
Invalid Entries
```

Pandas helps clean and analyze this data efficiently.

---

# Installation

```bash
pip install pandas
```

---

# Import Pandas

```python
import pandas as pd
```

---

# Core Data Structures

Pandas has two main data structures:

```text
Series
DataFrame
```

---

# 1. Series

## Theory

A Series is a one-dimensional labeled array.

Similar to:

```text
Single Column in Excel
```

---

## Example

```python
import pandas as pd

data = pd.Series([
    10,
    20,
    30
])

print(data)
```

Output:

```text
0    10
1    20
2    30
dtype: int64
```

---

# 2. DataFrame

## Theory

A DataFrame is a two-dimensional table.

Similar to:

```text
Excel Sheet
SQL Table
CSV File
```

---

## Example

```python
import pandas as pd

data = {
    "Name": ["Bittu", "Rahul"],
    "Age": [25, 24]
}

df = pd.DataFrame(data)

print(df)
```

Output:

```text
    Name  Age
0  Bittu   25
1  Rahul   24
```

---

# Creating DataFrames

## From Dictionary

```python
data = {
    "Name": ["Bittu", "Rahul"],
    "Salary": [50000, 60000]
}

df = pd.DataFrame(data)

print(df)
```

---

# Read CSV File

## Theory

Most common operation in Data Science.

---

employees.csv

```csv
Name,Age
Bittu,25
Rahul,24
```

---

## Read CSV

```python
df = pd.read_csv(
    "employees.csv"
)

print(df)
```

---

# Read Excel

```python
df = pd.read_excel(
    "employees.xlsx"
)
```

---

# View Data

## head()

Displays first rows.

```python
print(df.head())
```

Default:

```text
First 5 Rows
```

---

## tail()

Displays last rows.

```python
print(df.tail())
```

---

# Dataset Information

## info()

Shows:

```text
Columns
Data Types
Missing Values
```

---

Example:

```python
df.info()
```

---

# Statistical Summary

## describe()

Shows:

```text
Mean
Std
Min
Max
Percentiles
```

---

Example:

```python
df.describe()
```

---

# Selecting Columns

## Single Column

```python
print(df["Name"])
```

---

## Multiple Columns

```python
print(
    df[
        ["Name", "Age"]
    ]
)
```

---

# Selecting Rows

## loc[]

Label-based selection.

```python
print(df.loc[0])
```

---

## iloc[]

Position-based selection.

```python
print(df.iloc[0])
```

---

# Filtering Data

## Example

Employees age above 24.

```python
print(
    df[df["Age"] > 24]
)
```

Output:

```text
    Name Age
0  Bittu 25
```

---

# Sorting Data

## Ascending

```python
df.sort_values(
    "Age"
)
```

---

## Descending

```python
df.sort_values(
    "Age",
    ascending=False
)
```

---

# Add New Column

```python
df["Bonus"] = [
    5000,
    6000
]
```

---

Result:

```text
Name Age Bonus
```

---

# Update Column

```python
df["Age"] = df["Age"] + 1
```

---

# Delete Column

```python
df.drop(
    "Bonus",
    axis=1
)
```

---

# Missing Values

## Theory

Very common in real-world datasets.

---

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

---

# Fill Missing Values

```python
df.fillna(0)
```

---

## Fill with Mean

```python
df["Age"].fillna(
    df["Age"].mean()
)
```

---

# Remove Missing Values

```python
df.dropna()
```

---

# Duplicate Records

## Detect Duplicates

```python
df.duplicated()
```

---

## Remove Duplicates

```python
df.drop_duplicates()
```

---

# Rename Columns

```python
df.rename(
    columns={
        "Age":"Employee_Age"
    }
)
```

---

# Data Type Conversion

## Example

```python
df["Age"] = df["Age"].astype(
    int
)
```

---

# Aggregation Functions

## Sum

```python
df["Salary"].sum()
```

---

## Mean

```python
df["Salary"].mean()
```

---

## Maximum

```python
df["Salary"].max()
```

---

## Minimum

```python
df["Salary"].min()
```

---

## Count

```python
df["Salary"].count()
```

---

# GroupBy

## Theory

Groups data and performs aggregations.

---

Example Dataset

```text
Department Salary

IT        50000
IT        60000
HR        40000
```

---

## Example

```python
df.groupby(
    "Department"
)["Salary"].mean()
```

Output:

```text
HR 40000

IT 55000
```

---

# Value Counts

## Example

```python
df["Department"].value_counts()
```

Output:

```text
IT    2

HR    1
```

---

# Apply Function

## Example

```python
df["Salary"] = (
    df["Salary"]
    .apply(
        lambda x: x * 1.1
    )
)
```

Increase salary by 10%.

---

# Merge DataFrames

## Theory

Similar to SQL JOIN.

---

Employees

```text
ID Name
```

---

Salary

```text
ID Salary
```

---

## Example

```python
pd.merge(
    df1,
    df2,
    on="ID"
)
```

---

# Concatenate DataFrames

```python
pd.concat(
    [df1, df2]
)
```

---

# Export Data

## CSV

```python
df.to_csv(
    "output.csv",
    index=False
)
```

---

## Excel

```python
df.to_excel(
    "output.xlsx"
)
```

---

# Pandas in Data Cleaning

Common tasks:

```text
Remove Duplicates
Handle Missing Values
Convert Data Types
Fix Invalid Records
```

---

# Pandas in Machine Learning

Typical Workflow:

```text
Load Dataset
      ↓
Clean Data
      ↓
Feature Engineering
      ↓
EDA
      ↓
Train Model
```

---

# Insurance Example

Claims Dataset

```python
import pandas as pd

claims = pd.DataFrame({
    "ClaimAmount":[
        5000,
        10000,
        25000
    ],
    "Fraud":[
        0,
        0,
        1
    ]
})

print(claims)
```

---

Output

```text
ClaimAmount Fraud

5000        0

10000       0

25000       1
```

---

# Calculate Average Claim

```python
claims[
    "ClaimAmount"
].mean()
```

---

# Find Fraud Claims

```python
claims[
    claims["Fraud"] == 1
]
```

---

# AI Example

Training Dataset

```python
X = df[
    [
        "Age",
        "Salary"
    ]
]

y = df[
    "Target"
]
```

Used in:

```text
Scikit-Learn
TensorFlow
PyTorch
```

---

# Interview Questions

### Q1. What is Pandas?

```text
A Python library for data manipulation and analysis.
```

---

### Q2. Difference between Series and DataFrame?

```text
Series:
1-D Data

DataFrame:
2-D Tabular Data
```

---

### Q3. What is GroupBy?

```text
Used to group data and perform aggregations.
```

---

### Q4. How do you handle missing values?

```text
fillna()

dropna()
```

---

### Q5. Difference between loc and iloc?

```text
loc:
Label-Based

iloc:
Position-Based
```

---

# Learning Path

```text
Series
    ↓
DataFrame
    ↓
Read CSV
    ↓
Filtering
    ↓
Sorting
    ↓
Missing Values
    ↓
Duplicates
    ↓
GroupBy
    ↓
Merge
    ↓
Feature Engineering
    ↓
Machine Learning
```

# Most Important Pandas Topics for AI Engineers

```text
DataFrame
Read CSV
head()
info()
describe()
Filtering
Missing Values
Duplicates
GroupBy
Merge
Apply
Export Data
```

Pandas is used in:

```text
Data Cleaning
Feature Engineering
EDA
Machine Learning
Deep Learning
MLOps
LLMOps
AI Analytics
```

Mastering Pandas is essential before moving to:

```text
Scikit-Learn
Machine Learning
Deep Learning
Generative AI
```