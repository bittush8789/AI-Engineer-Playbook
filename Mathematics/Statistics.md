# Statistics for AI & Machine Learning

## What is Statistics?

Statistics is the science of collecting, organizing, analyzing, interpreting, and presenting data.

Statistics helps answer questions such as:

```text
What is the average claim amount?

What is the customer churn rate?

How accurate is a machine learning model?

What trends exist in the data?
```

---

# Why Statistics is Important in AI?

Machine Learning is built on statistics.

Applications:

```text
Data Analysis
Machine Learning
Deep Learning
A/B Testing
Forecasting
Fraud Detection
Recommendation Systems
```

---

# Statistics Workflow

```text
Collect Data
      ↓
Clean Data
      ↓
Analyze Data
      ↓
Find Patterns
      ↓
Build Models
      ↓
Make Decisions
```

---

# Types of Statistics

## 1. Descriptive Statistics

Describes and summarizes data.

Examples:

```text
Mean
Median
Mode
Variance
Standard Deviation
```

---

## 2. Inferential Statistics

Draw conclusions from sample data.

Examples:

```text
Hypothesis Testing
Confidence Intervals
A/B Testing
Predictions
```

---

# Example Dataset

```text
Claim Amounts

1000
2000
3000
4000
5000
```

---

# 1. Mean (Average)

## Theory

Mean is the average value of a dataset.

Formula:

```text
Sum of Values
--------------
Number of Values
```

---

## Example

Dataset:

```text
10, 20, 30, 40, 50
```

---

Calculation:

```text
(10+20+30+40+50)/5

= 30
```

---

## Python Example

```python
import numpy as np

data = [10,20,30,40,50]

print(np.mean(data))
```

Output:

```text
30.0
```

---

# 2. Median

## Theory

Median is the middle value after sorting data.

---

## Example

```text
10,20,30,40,50
```

Middle value:

```text
30
```

---

## Python

```python
import numpy as np

data = [10,20,30,40,50]

print(np.median(data))
```

Output:

```text
30.0
```

---

# 3. Mode

## Theory

Most frequently occurring value.

---

## Example

```text
10,20,20,30,40
```

Mode:

```text
20
```

---

## Python

```python
from statistics import mode

data = [10,20,20,30]

print(mode(data))
```

Output:

```text
20
```

---

# Mean vs Median vs Mode

| Metric | Meaning |
|----------|----------|
| Mean | Average |
| Median | Middle Value |
| Mode | Most Frequent |

---

# Example with Outlier

Dataset:

```text
10,20,30,40,1000
```

---

Mean:

```text
220
```

Median:

```text
30
```

---

Observation:

```text
Median handles outliers better.
```

---

# 4. Variance

## Theory

Variance measures how spread out data is from the mean.

---

### Formula


::contentReference[oaicite:0]{index=0}


---

## Interpretation

Low Variance:

```text
Data close to mean
```

High Variance:

```text
Data widely spread
```

---

## Example

Dataset A:

```text
49,50,51
```

Low variance.

---

Dataset B:

```text
10,50,90
```

High variance.

---

## Python

```python
import numpy as np

data = [10,20,30]

print(np.var(data))
```

---

# 5. Standard Deviation

## Theory

Standard deviation measures average distance from the mean.

---

Relationship:

```text
Standard Deviation

= √Variance
```

---

## Example

```python
import numpy as np

data = [10,20,30]

print(np.std(data))
```

---

## Interpretation

Small Value:

```text
Data tightly clustered
```

Large Value:

```text
Data highly dispersed
```

---

# 6. Sample Variance

## Theory

Used when calculating variance from a sample rather than the entire population.

---

### Formula


::contentReference[oaicite:1]{index=1}


---

## Python

```python
import numpy as np

data = [10,20,30]

print(np.var(data, ddof=1))
```

---

# Population vs Sample

## Population

Entire dataset.

Example:

```text
All Liberty Mutual Claims
```

---

## Sample

Subset of data.

Example:

```text
1000 Claims
```

---

# 7. Percentiles

## Theory

Percentile indicates the percentage of values below a given point.

---

## Example

90th Percentile:

```text
90% of values are below it.
```

---

## Python

```python
import numpy as np

data = [10,20,30,40,50]

print(
    np.percentile(
        data,
        90
    )
)
```

---

# 8. Quartiles

## Theory

Divide data into four equal parts.

---

```text
Q1 = 25%

Q2 = Median

Q3 = 75%
```

---

# Example

```text
10,20,30,40,50
```

---

# 9. Z-Score

## Theory

Measures how many standard deviations a value is away from the mean.

---

### Formula


::contentReference[oaicite:2]{index=2}


---

## Example

```text
Score = 90

Mean = 70

Std Dev = 10
```

---

Result:

```text
z = 2
```

Meaning:

```text
2 Standard Deviations Above Mean
```

---

# 10. Normal Distribution

## Theory

Most important distribution in statistics.

---

Shape:

```text
         /\
        /  \
       /    \
------/------\------
```

---

Properties:

```text
Mean = Median = Mode
```

---

# 68-95-99.7 Rule

Within:

```text
1 Std Dev → 68%

2 Std Dev → 95%

3 Std Dev → 99.7%
```

---

# Example

Customer Ages:

```text
Most customers near average age.
```

---

# 11. Skewness

## Theory

Measures asymmetry in data.

---

## Positive Skew

```text
Tail Right
```

Example:

```text
Income Distribution
```

---

## Negative Skew

```text
Tail Left
```

---

# 12. Correlation

## Theory

Measures relationship between variables.

Range:

```text
-1 to +1
```

---

## Positive Correlation

```text
Income ↑

Spending ↑
```

---

## Negative Correlation

```text
Price ↑

Demand ↓
```

---

## Python

```python
import pandas as pd

df.corr()
```

---

# Correlation Types

```text
+1 = Perfect Positive

0 = No Relationship

-1 = Perfect Negative
```

---

# 13. Covariance

## Theory

Shows whether variables move together.

---

Positive:

```text
Both increase together.
```

---

Negative:

```text
One increases,
other decreases.
```

---

# Correlation vs Covariance

| Correlation | Covariance |
|-------------|-------------|
| Standardized | Not Standardized |
| Range -1 to 1 | No Fixed Range |
| Easier Interpretation | Harder Interpretation |

---

# Statistics in Machine Learning

## Data Cleaning

Use:

```text
Mean
Median
Mode
```

---

## Feature Engineering

Use:

```text
Correlation
Variance
```

---

## Outlier Detection

Use:

```text
Z-Score
Percentiles
```

---

# Statistics in Deep Learning

Used in:

```text
Weight Initialization
Normalization
Batch Normalization
```

---

# Insurance Example

Claim Amounts:

```text
1000
1500
2000
50000
```

---

Mean:

```text
Influenced by Outlier
```

---

Median:

```text
More Reliable
```

---

Use Cases:

```text
Fraud Detection
Claim Severity Prediction
Risk Analysis
```

---

# Python Example

```python
import numpy as np

claims = [
    1000,
    1500,
    2000,
    50000
]

print("Mean:",
      np.mean(claims))

print("Median:",
      np.median(claims))

print("Std:",
      np.std(claims))
```

---

# Interview Questions

### Q1. What is Statistics?

```text
The science of collecting, analyzing, and interpreting data.
```

---

### Q2. Difference between Mean and Median?

```text
Mean:
Average value.

Median:
Middle value.
```

---

### Q3. What is Variance?

```text
Measure of data spread.
```

---

### Q4. What is Standard Deviation?

```text
Square root of variance.
```

---

### Q5. What is Correlation?

```text
Measure of relationship between variables.
```

---

# Learning Path

```text
Descriptive Statistics
        ↓
Mean
        ↓
Median
        ↓
Mode
        ↓
Variance
        ↓
Standard Deviation
        ↓
Percentiles
        ↓
Z-Score
        ↓
Normal Distribution
        ↓
Correlation
        ↓
Inferential Statistics
```

# Most Important Statistics Topics for AI Engineers

```text
Mean
Median
Mode
Variance
Standard Deviation
Percentiles
Z-Score
Normal Distribution
Correlation
Covariance
```

These concepts are heavily used in:

```text
Machine Learning
Deep Learning
Feature Engineering
EDA
Data Science
Fraud Detection
Predictive Analytics
Generative AI
LLMs
```