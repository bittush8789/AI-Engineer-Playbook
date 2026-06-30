# Neural Networks

## What are Neural Networks?

Neural Networks are Machine Learning models inspired by the structure of the human brain.

They consist of interconnected nodes called **neurons** that learn patterns from data.

---

# Why Neural Networks?

Traditional Machine Learning works well for structured data.

However, for complex problems such as:

```text
Image Recognition
Speech Recognition
Natural Language Processing
Generative AI
Large Language Models
```

Neural Networks perform significantly better.

---

# Human Brain vs Neural Network

Human Brain:

```text
Neurons
     ↓
Connections
     ↓
Decision
```

Neural Network:

```text
Artificial Neurons
         ↓
Connections (Weights)
         ↓
Prediction
```

---

# Basic Structure

A Neural Network contains:

```text
Input Layer
Hidden Layer(s)
Output Layer
```

---

# Visualization

```text
Input Layer

x1    x2    x3
 |     |     |
 ▼     ▼     ▼

Hidden Layer

 ○-----○-----○
 |     |     |
 ○-----○-----○

       ▼

Output Layer

       ○
```

---

# Components of Neural Networks

```text
Neurons
Weights
Bias
Activation Functions
Loss Function
Optimizer
```

---

# 1. Neuron

## Theory

A neuron is the smallest computational unit.

It receives inputs, performs calculations, and produces output.

---

## Example

Input:

```text
Age = 25

Salary = 50000
```

Neuron:

```text
Calculation
```

Output:

```text
Loan Approved
```

---

# Mathematical Representation

A neuron computes:

```text
Output

=

(Inputs × Weights)
+
Bias
```

---

Formula:

```text
z = w1x1 + w2x2 + ... + b
```

Where:

```text
x = Inputs

w = Weights

b = Bias
```

---

# Example

```text
x1 = 2

w1 = 3

Bias = 1
```

Calculation:

```text
z = (2 × 3) + 1

= 7
```

---

# 2. Weights

## Theory

Weights determine the importance of each feature.

---

Example:

Insurance Fraud Model

```text
Claim Amount
Vehicle Age
Driver History
```

---

Weight Importance:

```text
Claim Amount → High Weight

Vehicle Color → Low Weight
```

---

During training:

```text
Weights Continuously Update
```

---

# 3. Bias

## Theory

Bias shifts the output.

---

Without Bias:

```text
Model Too Restrictive
```

---

With Bias:

```text
More Flexible Learning
```

---

# Neural Network Layers

## Input Layer

Receives data.

---

Example:

```text
Age

Salary

Credit Score
```

---

# Hidden Layer

Performs learning.

---

Example:

```text
Pattern Detection

Feature Extraction

Relationship Learning
```

---

# Output Layer

Produces final prediction.

---

Examples:

```text
Fraud

Not Fraud
```

or

```text
House Price
```

---

# Forward Propagation

## Theory

Information flows from input to output.

---

Workflow:

```text
Input
   ↓
Hidden Layer
   ↓
Output Layer
```

---

Example:

```text
Customer Data
      ↓
Network
      ↓
Fraud Prediction
```

---

# Activation Function

## Why Needed?

Without activation functions:

```text
Neural Network
=
Linear Model
```

---

Activation functions introduce:

```text
Non-Linearity
```

allowing networks to learn complex patterns.

---

# Common Activation Functions

```text
Sigmoid
Tanh
ReLU
Leaky ReLU
Softmax
```

---

# ReLU

Most commonly used.

Formula:

```text
f(x) = max(0,x)
```

---

Example:

```text
Input = -5

Output = 0
```

---

Example:

```text
Input = 8

Output = 8
```

---

Visualization:

```text
     /
    /
___/
```

---

# Sigmoid

Formula:

```text
1
---------
1 + e^-x
```

---

Output Range:

```text
0 to 1
```

---

Used in:

```text
Binary Classification
```

---

# Softmax

Used for:

```text
Multi-Class Classification
```

---

Output:

```text
Probabilities
```

Example:

```text
Cat = 0.70

Dog = 0.20

Bird = 0.10
```

---

# Loss Function

## Theory

Measures prediction error.

---

Example:

Actual:

```text
Fraud
```

Prediction:

```text
Not Fraud
```

---

Loss:

```text
High
```

---

Goal:

```text
Minimize Loss
```

---

# Common Loss Functions

## Regression

```text
Mean Squared Error (MSE)
```

---

## Classification

```text
Cross Entropy Loss
```

---

# Backpropagation

## Theory

Backpropagation is the learning mechanism of Neural Networks.

---

Purpose:

```text
Calculate Error

Update Weights
```

---

Workflow:

```text
Prediction
      ↓
Calculate Loss
      ↓
Backpropagation
      ↓
Update Weights
```

---

# Gradient Descent

Used with Backpropagation.

---

Formula:

```text
New Weight

=

Old Weight

-

Learning Rate × Gradient
```

---

Goal:

```text
Reduce Loss
```

---

# Training Process

```text
Initialize Weights
        ↓
Forward Propagation
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

# Epoch

## Theory

One complete pass through the dataset.

---

Example:

Dataset:

```text
10,000 Records
```

---

Epoch:

```text
All 10,000 Processed Once
```

---

# Batch Size

## Theory

Number of samples processed together.

---

Example:

```text
Batch Size = 32
```

---

Meaning:

```text
32 Records At A Time
```

---

# Learning Rate

Controls:

```text
Weight Update Size
```

---

Small:

```text
Slow Learning
```

---

Large:

```text
Overshooting
```

---

Typical Values:

```text
0.1

0.01

0.001
```

---

# Deep Neural Networks

## Theory

Networks with many hidden layers.

---

Visualization:

```text
Input
  ↓

Hidden Layer 1

  ↓

Hidden Layer 2

  ↓

Hidden Layer 3

  ↓

Output
```

---

Called:

```text
Deep Learning
```

---

# Neural Networks in AI

Used in:

```text
Computer Vision
Speech Recognition
NLP
Recommendation Systems
Generative AI
```

---

# Insurance Example

## Fraud Detection

Inputs:

```text
Claim Amount

Policy Age

Driver History
```

---

Output:

```text
Fraud Probability
```

---

Neural Network learns:

```text
Fraud Patterns
```

from historical claims.

---

# Insurance Example 2

## Claim Severity Prediction

Features:

```text
Vehicle Age

Accident Type

Coverage Type
```

---

Output:

```text
Severity Score
```

---

# Python Example (TensorFlow)

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense

model = Sequential()

model.add(
    Dense(
        16,
        activation="relu",
        input_shape=(10,)
    )
)

model.add(
    Dense(
        8,
        activation="relu"
    )
)

model.add(
    Dense(
        1,
        activation="sigmoid"
    )
)

model.compile(
    optimizer="adam",
    loss="binary_crossentropy"
)
```

---

# Advantages

```text
Learns Complex Patterns
High Accuracy
Automatic Feature Learning
Works with Large Data
```

---

# Disadvantages

```text
Requires Large Data
Computationally Expensive
Less Interpretable
Long Training Time
```

---

# Interview Questions

### Q1. What is a Neural Network?

```text
A machine learning model composed of interconnected neurons that learn patterns from data.
```

---

### Q2. What is a Neuron?

```text
The basic computational unit of a neural network.
```

---

### Q3. Why do we use Activation Functions?

```text
To introduce non-linearity and learn complex patterns.
```

---

### Q4. What is Backpropagation?

```text
The algorithm used to calculate errors and update weights.
```

---

### Q5. What is an Epoch?

```text
One complete pass through the training dataset.
```

---

# Learning Path

```text
Neurons
    ↓
Weights & Bias
    ↓
Activation Functions
    ↓
Forward Propagation
    ↓
Loss Functions
    ↓
Backpropagation
    ↓
Gradient Descent
    ↓
Deep Neural Networks
    ↓
CNN
    ↓
RNN
    ↓
Transformers
```

# Most Important Topics for AI Engineers

```text
Neurons
Weights
Bias
Layers
Activation Functions
Forward Propagation
Loss Functions
Backpropagation
Gradient Descent
Epochs
Batch Size
Learning Rate
```

Neural Networks form the foundation of:

```text
Deep Learning
Computer Vision
Natural Language Processing
Generative AI
Large Language Models (LLMs)
Agentic AI
Multimodal AI
```

Modern systems such as GPT, Claude, and Gemini are ultimately built on large-scale neural network architectures.