# NumPy (Numerical Python)

## What is NumPy?

NumPy (Numerical Python) is the fundamental library for numerical computing in Python.

It provides:

- Fast Mathematical Operations
- Multi-Dimensional Arrays
- Matrix Operations
- Linear Algebra Functions
- Statistical Functions
- Random Number Generation

Almost every AI/ML library is built on top of NumPy.

Examples:

```text
Pandas
Scikit-Learn
TensorFlow
PyTorch
OpenCV
SciPy
```

---

# Why NumPy?

Python Lists are slow for large-scale numerical computations.

NumPy provides:

```text
Faster Computation
Less Memory Usage
Vectorized Operations
Mathematical Functions
```

---

# Installation

```bash
pip install numpy
```

---

# Import NumPy

```python
import numpy as np
```

---

# What is an Array?

## Theory

An Array is a collection of elements stored in contiguous memory locations.

NumPy's core object is:

```text
ndarray
```

(ndimensional array)

---

## Python List

```python
numbers = [1, 2, 3, 4]
```

---

## NumPy Array

```python
import numpy as np

numbers = np.array([1, 2, 3, 4])

print(numbers)
```

Output:

```text
[1 2 3 4]
```

---

# Why Arrays Matter in AI?

Dataset:

```text
Age Salary

25 50000
30 70000
35 90000
```

Stored as:

```python
[
 [25,50000],
 [30,70000],
 [35,90000]
]
```

Machine Learning algorithms work directly with arrays.

---

# Creating Arrays

## 1D Array

```python
import numpy as np

arr = np.array([1, 2, 3, 4])

print(arr)
```

Output:

```text
[1 2 3 4]
```

---

# 2D Array

```python
arr = np.array([
    [1,2],
    [3,4]
])

print(arr)
```

Output:

```text
[[1 2]
 [3 4]]
```

---

# 3D Array

```python
arr = np.array([
    [
        [1,2],
        [3,4]
    ]
])

print(arr)
```

---

# Array Dimensions

## ndim

Returns number of dimensions.

```python
arr = np.array([
    [1,2],
    [3,4]
])

print(arr.ndim)
```

Output:

```text
2
```

---

# Shape

## Theory

Returns rows and columns.

```python
print(arr.shape)
```

Output:

```text
(2, 2)
```

Meaning:

```text
2 Rows
2 Columns
```

---

# Size

## Theory

Total number of elements.

```python
print(arr.size)
```

Output:

```text
4
```

---

# Data Types

## dtype

Returns data type.

```python
arr = np.array([1,2,3])

print(arr.dtype)
```

Output:

```text
int64
```

---

# Creating Special Arrays

## Zeros

```python
arr = np.zeros((2,3))

print(arr)
```

Output:

```text
[[0. 0. 0.]
 [0. 0. 0.]]
```

---

## Ones

```python
arr = np.ones((2,3))

print(arr)
```

Output:

```text
[[1. 1. 1.]
 [1. 1. 1.]]
```

---

## Identity Matrix

```python
arr = np.eye(3)

print(arr)
```

Output:

```text
[[1. 0. 0.]
 [0. 1. 0.]
 [0. 0. 1.]]
```

---

# Range Functions

## arange()

Similar to Python range().

```python
arr = np.arange(1,10)

print(arr)
```

Output:

```text
[1 2 3 4 5 6 7 8 9]
```

---

## linspace()

Creates evenly spaced numbers.

```python
arr = np.linspace(
    0,
    10,
    5
)

print(arr)
```

Output:

```text
[0.  2.5  5.  7.5 10.]
```

---

# Array Indexing

## Example

```python
arr = np.array([
    10,20,30,40
])

print(arr[0])
```

Output:

```text
10
```

---

# Negative Indexing

```python
print(arr[-1])
```

Output:

```text
40
```

---

# Slicing

```python
arr = np.array([
    10,20,30,40,50
])

print(arr[1:4])
```

Output:

```text
[20 30 40]
```

---

# 2D Indexing

```python
arr = np.array([
    [1,2],
    [3,4]
])

print(arr[0,1])
```

Output:

```text
2
```

---

# Array Operations

## Addition

```python
a = np.array([1,2,3])

b = np.array([4,5,6])

print(a + b)
```

Output:

```text
[5 7 9]
```

---

# Subtraction

```python
print(a - b)
```

Output:

```text
[-3 -3 -3]
```

---

# Multiplication

```python
print(a * b)
```

Output:

```text
[ 4 10 18 ]
```

---

# Division

```python
print(a / b)
```

Output:

```text
[0.25 0.4 0.5]
```

---

# Scalar Operations

```python
arr = np.array([1,2,3])

print(arr * 5)
```

Output:

```text
[ 5 10 15 ]
```

---

# Aggregation Functions

## Sum

```python
arr = np.array([1,2,3])

print(np.sum(arr))
```

Output:

```text
6
```

---

## Mean

```python
print(np.mean(arr))
```

Output:

```text
2.0
```

---

## Maximum

```python
print(np.max(arr))
```

Output:

```text
3
```

---

## Minimum

```python
print(np.min(arr))
```

Output:

```text
1
```

---

# Statistical Functions

## Standard Deviation

```python
arr = np.array([
    10,20,30
])

print(np.std(arr))
```

---

## Variance

```python
print(np.var(arr))
```

---

# Reshaping Arrays

## Theory

Change array dimensions.

---

## Example

```python
arr = np.array([
    1,2,3,4,5,6
])

print(
    arr.reshape(2,3)
)
```

Output:

```text
[[1 2 3]
 [4 5 6]]
```

---

# Flatten Array

```python
arr = np.array([
    [1,2],
    [3,4]
])

print(arr.flatten())
```

Output:

```text
[1 2 3 4]
```

---

# Matrix Operations

## Matrix Creation

```python
A = np.array([
    [1,2],
    [3,4]
])
```

---

# Matrix Addition

```python
print(A + A)
```

Output:

```text
[[2 4]
 [6 8]]
```

---

# Matrix Multiplication

```python
print(np.matmul(A, A))
```

Output:

```text
[[ 7 10]
 [15 22]]
```

---

# Matrix Transpose

```python
print(A.T)
```

Output:

```text
[[1 3]
 [2 4]]
```

---

# Dot Product

## Theory

Measures similarity between vectors.

---

## Example

```python
A = np.array([1,2])

B = np.array([3,4])

print(np.dot(A,B))
```

Output:

```text
11
```

---

# Random Module

## Random Numbers

```python
print(
    np.random.rand(3)
)
```

Output:

```text
[0.23 0.91 0.55]
```

---

## Random Integers

```python
print(
    np.random.randint(
        1,
        10,
        5
    )
)
```

---

# Boolean Filtering

```python
arr = np.array([
    10,20,30,40
])

print(
    arr[arr > 20]
)
```

Output:

```text
[30 40]
```

---

# Broadcasting

## Theory

Allows operations between arrays of different shapes.

---

## Example

```python
arr = np.array([
    1,2,3
])

print(arr + 10)
```

Output:

```text
[11 12 13]
```

---

# NumPy in Machine Learning

Dataset Example:

```python
import numpy as np

X = np.array([
    [25,50000],
    [30,70000],
    [35,90000]
])

y = np.array([
    0,
    1,
    1
])
```

Used in:

```text
Linear Regression
Logistic Regression
Decision Trees
Neural Networks
```

---

# NumPy in Deep Learning

Neural Network:

```text
Input Matrix
      ×
Weight Matrix
      =
Output
```

All computations are matrix operations.

---

# Insurance Example

Claim Dataset:

```python
claims = np.array([
    [5000,1],
    [10000,0],
    [25000,1]
])
```

Columns:

```text
Claim Amount
Fraud Flag
```

Used for:

```text
Fraud Detection
Severity Prediction
Risk Analysis
```

---

# Interview Questions

### Q1. What is NumPy?

```text
A Python library for numerical computing and array processing.
```

---

### Q2. What is ndarray?

```text
NumPy's multidimensional array object.
```

---

### Q3. Difference between List and NumPy Array?

```text
NumPy arrays are faster and more memory efficient.
```

---

### Q4. What is Broadcasting?

```text
Applying operations on arrays with different shapes.
```

---

### Q5. What is the use of np.dot()?

```text
Computes dot product between vectors or matrices.
```

---

# Learning Path

```text
NumPy Basics
      ↓
Arrays
      ↓
Indexing
      ↓
Slicing
      ↓
Array Operations
      ↓
Aggregation Functions
      ↓
Reshaping
      ↓
Matrix Operations
      ↓
Broadcasting
      ↓
Linear Algebra
      ↓
Machine Learning
```

# Most Important NumPy Topics for AI Engineers

```text
ndarray
Array Creation
Indexing
Slicing
Broadcasting
Aggregation Functions
Reshaping
Dot Product
Matrix Multiplication
Random Module
```

NumPy is the foundation of:

```text
Pandas
Scikit-Learn
TensorFlow
PyTorch
Computer Vision
Machine Learning
Deep Learning
Generative AI
```

Mastering NumPy is one of the first and most important steps toward becoming an AI Engineer.