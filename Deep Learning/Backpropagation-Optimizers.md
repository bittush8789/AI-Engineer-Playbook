# Backpropagation

## What is Backpropagation?

Backpropagation (Backward Propagation of Errors) is the core learning algorithm used to train Neural Networks.

Its purpose is:

```text
Calculate Error
      ↓
Find Cause of Error
      ↓
Update Weights
      ↓
Reduce Loss
```

Without Backpropagation:

```text
Neural Networks Cannot Learn
```

---

# Why Backpropagation?

Suppose a Neural Network predicts:

```text
Fraud Probability = 0.20
```

Actual:

```text
Fraud = 1
```

Prediction is wrong.

The network needs to know:

```text
Which Weights Caused The Error?
```

Backpropagation finds the answer.

---

# Neural Network Training Process

```text
Input Data
      ↓
Forward Propagation
      ↓
Prediction
      ↓
Calculate Loss
      ↓
Backpropagation
      ↓
Update Weights
      ↓
Repeat
```

---

# Forward Propagation

## Theory

Data moves from:

```text
Input Layer
      ↓
Hidden Layer
      ↓
Output Layer
```

---

Example:

```text
Age = 25

Salary = 50000
```

---

Prediction:

```text
Loan Approved
```

---

# Loss Calculation

## Theory

Loss measures prediction error.

---

Example:

Actual:

```text
1
```

Prediction:

```text
0.7
```

Loss:

```text
0.3 Error
```

---

Goal:

```text
Minimize Loss
```

---

# Backward Propagation

## Theory

Error travels backward through the network.

---

Visualization:

```text
Input
  ↓
Hidden Layer
  ↓
Output
  ↓
Loss
  ↑
Backpropagation
```

---

Purpose:

```text
Calculate Gradients
```

for every weight.

---

# Gradient

## Theory

Gradient indicates:

```text
How Much A Weight Contributes To Error
```

---

Large Gradient:

```text
Weight Needs Large Update
```

---

Small Gradient:

```text
Weight Needs Small Update
```

---

# Chain Rule

Backpropagation uses:

```text
Chain Rule
```

from Calculus.

---

Example:

```text
Output
   ↓
Hidden Layer
   ↓
Input Layer
```

---

Error is propagated backward using derivatives.

---

# Backpropagation Workflow

```text
Forward Pass
      ↓
Prediction
      ↓
Loss Calculation
      ↓
Compute Gradients
      ↓
Propagate Error Backward
      ↓
Update Weights
```

---

# Mathematical Idea

Suppose:

```text
Loss = L

Weight = W
```

---

Backpropagation computes:

```text
dL/dW
```

Meaning:

```text
How Loss Changes
When Weight Changes
```

---

# Weight Update Formula

```text
New Weight

=

Old Weight

-

Learning Rate × Gradient
```

---

Example

Weight:

```text
0.5
```

Gradient:

```text
0.2
```

Learning Rate:

```text
0.1
```

---

Update:

```text
0.5 - (0.1 × 0.2)

= 0.48
```

---

# Why Backpropagation Works

Repeated updates:

```text
Reduce Error
Improve Predictions
Learn Patterns
```

---

# Example

Fraud Detection

Input:

```text
Claim Amount
Driver Age
Vehicle Age
```

---

Prediction:

```text
Not Fraud
```

Actual:

```text
Fraud
```

---

Backpropagation:

```text
Calculate Error
      ↓
Update Weights
      ↓
Improve Future Predictions
```

---

# Problems in Backpropagation

## Vanishing Gradient

Gradients become:

```text
Very Small
```

---

Result:

```text
Slow Learning
```

---

Common in:

```text
Sigmoid
Tanh
```

---

# Exploding Gradient

Gradients become:

```text
Very Large
```

---

Result:

```text
Unstable Training
```

---

Solution:

```text
Gradient Clipping
Better Optimizers
```

---

# Optimizers

## What is an Optimizer?

An Optimizer is an algorithm that updates weights using gradients calculated by Backpropagation.

---

Relationship:

```text
Backpropagation
      ↓
Calculates Gradients

Optimizer
      ↓
Updates Weights
```

---

# Why Optimizers?

Without optimizers:

```text
Learning Is Slow
```

Optimizers help:

```text
Faster Training
Lower Loss
Better Accuracy
```

---

# Types of Optimizers

```text
Gradient Descent
SGD
Momentum
RMSProp
Adam
AdamW
```

---

# 1. Gradient Descent

## Theory

Basic optimizer.

---

Workflow:

```text
Calculate Gradient
      ↓
Update Weight
```

---

Formula:

```text
W = W - η × Gradient
```

Where:

```text
η = Learning Rate
```

---

# Advantages

```text
Simple
Easy To Understand
```

---

# Disadvantages

```text
Slow
Can Get Stuck
```

---

# 2. Stochastic Gradient Descent (SGD)

## Theory

Updates weights after each sample.

---

Workflow:

```text
One Sample
     ↓
Update
```

---

Advantages:

```text
Fast
Less Memory
```

---

Disadvantages:

```text
Noisy Updates
```

---

# Python Example

```python
optimizer = SGD(
    learning_rate=0.01
)
```

---

# 3. Momentum

## Theory

Adds previous movement information.

---

Example:

Ball Rolling Downhill

```text
Previous Speed
      +
Current Gradient
```

---

Benefits:

```text
Faster Convergence
Reduced Oscillation
```

---

# Momentum Formula

```text
Current Update

=

Previous Update
+
Gradient
```

---

# 4. RMSProp

## Theory

Adaptive Learning Rate optimizer.

---

Idea:

```text
Large Gradients
      ↓
Smaller Steps

Small Gradients
      ↓
Larger Steps
```

---

Benefits:

```text
Stable Learning
Faster Training
```

---

# Applications

```text
RNNs
LSTMs
```

---

# 5. Adam Optimizer

## Most Popular Optimizer

Adam stands for:

```text
Adaptive Moment Estimation
```

---

Combines:

```text
Momentum
+
RMSProp
```

---

Benefits:

```text
Fast
Stable
Adaptive
```

---

Most Deep Learning projects use:

```text
Adam
```

---

# Advantages

```text
Excellent Performance
Minimal Tuning
Works Across Many Problems
```

---

# Python Example

```python
from tensorflow.keras.optimizers import Adam

optimizer = Adam(
    learning_rate=0.001
)
```

---

# 6. AdamW

## Improved Adam

Used heavily in:

```text
Transformers
LLMs
```

---

Benefits:

```text
Better Generalization
Reduced Overfitting
```

---

Used by:

```text
GPT Models
BERT
Llama
Modern LLMs
```

---

# Optimizer Comparison

| Optimizer | Speed | Popularity |
|------------|---------|---------|
| Gradient Descent | Slow | Low |
| SGD | Medium | Medium |
| Momentum | Fast | High |
| RMSProp | Fast | High |
| Adam | Very Fast | Very High |
| AdamW | Very Fast | Highest |

---

# Deep Learning Workflow

```text
Input
  ↓
Forward Pass
  ↓
Prediction
  ↓
Loss
  ↓
Backpropagation
  ↓
Gradients
  ↓
Optimizer
  ↓
Weight Update
```

---

# Insurance Example

## Claim Fraud Detection

Inputs:

```text
Claim Amount
Policy Age
Vehicle Age
```

---

Prediction:

```text
Fraud Probability
```

---

Training:

```text
Forward Pass
      ↓
Loss
      ↓
Backpropagation
      ↓
Adam Optimizer
      ↓
Update Weights
```

---

# Transformers & LLMs

Training GPT-style models:

```text
Forward Pass
      ↓
Cross Entropy Loss
      ↓
Backpropagation
      ↓
AdamW Optimizer
      ↓
Update Billions Of Weights
```

---

# Interview Questions

### Q1. What is Backpropagation?

```text
The algorithm used to calculate gradients and propagate errors backward through a neural network.
```

---

### Q2. Why is Backpropagation important?

```text
It enables neural networks to learn by updating weights.
```

---

### Q3. What is an Optimizer?

```text
An algorithm that updates model weights using gradients.
```

---

### Q4. Why is Adam popular?

```text
It combines Momentum and RMSProp, providing fast and stable convergence.
```

---

### Q5. Difference between Backpropagation and Optimizer?

```text
Backpropagation:
Calculates Gradients.

Optimizer:
Updates Weights.
```

---

# Learning Path

```text
Loss Functions
      ↓
Derivatives
      ↓
Chain Rule
      ↓
Gradients
      ↓
Backpropagation
      ↓
Gradient Descent
      ↓
SGD
      ↓
Momentum
      ↓
RMSProp
      ↓
Adam
      ↓
AdamW
```

# Most Important Topics for AI Engineers

```text
Forward Propagation
Loss Functions
Gradients
Chain Rule
Backpropagation
Gradient Descent
SGD
Momentum
RMSProp
Adam
AdamW
```

These concepts are fundamental to:

```text
Neural Networks
CNNs
RNNs
LSTMs
Transformers
Large Language Models (LLMs)
Generative AI
Multimodal AI
```

Every modern AI system—from image classifiers to LLMs—learns through the combination of **Backpropagation + Optimizers**.