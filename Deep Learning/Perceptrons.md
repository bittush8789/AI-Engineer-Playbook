# Perceptrons

## What is a Perceptron?

A Perceptron is the simplest form of an Artificial Neural Network and is considered the building block of modern Neural Networks.

It was introduced by :contentReference[oaicite:0]{index=0} in 1957.

---

# Why Perceptrons?

A perceptron learns how to make decisions by finding a relationship between inputs and outputs.

Example:

```text
Loan Approval

Age
Salary
Credit Score
      ↓
Approve / Reject
```

---

# Human Brain Analogy

Human Brain:

```text
Neuron
   ↓
Processes Signals
   ↓
Decision
```

---

Artificial Neural Network:

```text
Perceptron
      ↓
Processes Inputs
      ↓
Prediction
```

---

# Structure of a Perceptron

A perceptron contains:

```text
Inputs
Weights
Bias
Activation Function
Output
```

---

# Architecture

```text
x1 ----\
        \
x2 ----- > [ Perceptron ] ----> Output
        /
x3 ----/

```

---

# Components of a Perceptron

## 1. Inputs

Inputs are features provided to the model.

Example:

```text
Age
Salary
Experience
```

---

Represented as:

```text
x1
x2
x3
```

---

# 2. Weights

## Theory

Weights represent the importance of each feature.

---

Example:

```text
Salary → High Importance

Favorite Color → Low Importance
```

---

Represented as:

```text
w1
w2
w3
```

---

# 3. Bias

## Theory

Bias helps shift the decision boundary.

---

Without Bias:

```text
Limited Learning
```

---

With Bias:

```text
Flexible Learning
```

---

Represented as:

```text
b
```

---

# Mathematical Formula

A perceptron computes:

```text
z

=

w1x1
+
w2x2
+
w3x3
+
b
```

---

This is called:

```text
Weighted Sum
```

---

# Example

Inputs:

```text
x1 = 2

x2 = 3
```

Weights:

```text
w1 = 4

w2 = 5
```

Bias:

```text
b = 1
```

---

Calculation:

```text
z

=

(2 × 4)

+

(3 × 5)

+

1

=

24
```

---

# Activation Function

## Theory

After calculating the weighted sum, the perceptron applies an activation function.

---

Purpose:

```text
Make Decision
```

---

# Step Function

Original perceptrons used:

```text
Step Function
```

---

Formula:

```text
Output = 1

if z >= 0

Output = 0

if z < 0
```

---

# Example

```text
z = 10
```

Output:

```text
1
```

---

Example:

```text
z = -5
```

Output:

```text
0
```

---

# Perceptron Decision Boundary

Suppose:

```text
Output = Loan Approved
```

---

Rule:

```text
If Score > Threshold

Approve
```

---

Otherwise:

```text
Reject
```

---

Visualization

```text
Approved

● ● ● ●

-----------
Boundary

▲ ▲ ▲ ▲

Rejected
```

---

# Working of a Perceptron

## Step 1

Receive inputs.

---

```text
Age

Salary
```

---

## Step 2

Multiply inputs by weights.

---

```text
Input × Weight
```

---

## Step 3

Add weighted values.

---

```text
Weighted Sum
```

---

## Step 4

Add Bias.

---

## Step 5

Apply Activation Function.

---

## Step 6

Generate Output.

---

# Complete Workflow

```text
Inputs
   ↓
Multiply by Weights
   ↓
Add Bias
   ↓
Activation Function
   ↓
Output
```

---

# Training a Perceptron

Goal:

```text
Adjust Weights
Minimize Errors
```

---

Workflow:

```text
Prediction
     ↓
Calculate Error
     ↓
Update Weights
     ↓
Repeat
```

---

# Weight Update Rule

Perceptron Learning Rule:

```text
New Weight

=

Old Weight

+

Learning Rate
×
Error
×
Input
```

---

# Example

Current Weight:

```text
0.5
```

Error:

```text
1
```

Learning Rate:

```text
0.1
```

Input:

```text
2
```

---

Update:

```text
0.5

+

0.1 × 1 × 2

=

0.7
```

---

# Single Layer Perceptron

## Theory

Contains:

```text
Input Layer

Output Layer
```

No hidden layer.

---

Architecture

```text
Input
  ↓
Output
```

---

# Limitation of Single Layer Perceptron

Can only solve:

```text
Linearly Separable Problems
```

---

Example:

```text
Yes

No

Approved

Rejected
```

---

Cannot solve complex problems.

---

# XOR Problem

Input:

| A | B | Output |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

---

Single Layer Perceptron:

```text
Fails
```

---

Reason:

```text
Not Linearly Separable
```

---

# Multi-Layer Perceptron (MLP)

To solve complex problems:

```text
Input Layer
      ↓
Hidden Layer
      ↓
Output Layer
```

---

Architecture

```text
Input
  ↓

Hidden Layer

  ↓

Output
```

---

MLPs can solve:

```text
Images
Text
Speech
Fraud Detection
```

---

# Perceptron vs Neural Network

| Perceptron | Neural Network |
|------------|------------|
| Single Neuron | Many Neurons |
| Simple | Complex |
| One Layer | Multiple Layers |
| Linear Problems | Non-Linear Problems |

---

# Python Example

## Using Scikit-Learn

```python
from sklearn.linear_model import Perceptron

model = Perceptron()

model.fit(
    X_train,
    y_train
)

predictions = model.predict(
    X_test
)
```

---

# Insurance Example

## Claim Approval

Features:

```text
Claim Amount

Policy Age

Coverage Type
```

---

Output:

```text
Approve

Reject
```

---

Perceptron learns:

```text
Decision Boundary
```

between approval and rejection.

---

# Insurance Example 2

## Fraud Detection

Inputs:

```text
Claim Amount

Driver History

Vehicle Age
```

---

Output:

```text
Fraud

Not Fraud
```

---

Perceptron learns simple fraud patterns.

---

# Advantages

```text
Simple
Fast
Easy to Understand
Foundation of Neural Networks
```

---

# Disadvantages

```text
Cannot Solve XOR
Only Linear Problems
Limited Capability
```

---

# Interview Questions

### Q1. What is a Perceptron?

```text
A single artificial neuron used for binary classification tasks.
```

---

### Q2. What are the components of a Perceptron?

```text
Inputs
Weights
Bias
Activation Function
Output
```

---

### Q3. What is the Perceptron Learning Rule?

```text
A rule used to update weights based on prediction error.
```

---

### Q4. Why does a Single Layer Perceptron fail on XOR?

```text
Because XOR is not linearly separable.
```

---

### Q5. What is a Multi-Layer Perceptron?

```text
A neural network containing one or more hidden layers.
```

---

# Learning Path

```text
Perceptron
     ↓
Weights & Bias
     ↓
Activation Functions
     ↓
Single Layer Perceptron
     ↓
XOR Problem
     ↓
Multi-Layer Perceptron
     ↓
Backpropagation
     ↓
Deep Neural Networks
```

# Most Important Topics for AI Engineers

```text
Perceptron Architecture
Weights
Bias
Activation Functions
Decision Boundary
Learning Rule
Single Layer Perceptron
Multi-Layer Perceptron
XOR Problem
```

The Perceptron is the foundation of:

```text
Neural Networks
Deep Learning
Computer Vision
NLP
Transformers
Large Language Models
Generative AI
```

Understanding the Perceptron is the first step toward understanding how modern AI systems learn from data.