# Activation Functions

## What are Activation Functions?

An Activation Function is a mathematical function applied to the output of a neuron that determines whether the neuron should be activated or not.

Without activation functions:

```text
Neural Network
=
Linear Model
```

which means it cannot learn complex patterns.

---

# Why Do We Need Activation Functions?

Suppose we have a Neural Network:

```text
Input
  ↓
Hidden Layer
  ↓
Output
```

Without activation functions:

```text
Output
=
Linear Combination of Inputs
```

No matter how many layers we add, the network behaves like a simple linear model.

---

Activation Functions introduce:

```text
Non-Linearity
```

which allows Neural Networks to learn:

```text
Images
Text
Speech
Fraud Patterns
Complex Relationships
```

---

# Role of Activation Functions

```text
Input
   ↓
Weighted Sum
   ↓
Activation Function
   ↓
Output
```

---

Mathematically:

```text
z = wx + b
```

Activation:

```text
a = f(z)
```

Where:

```text
z = Weighted Sum

f = Activation Function

a = Output
```

---

# Types of Activation Functions

```text
Step Function
Linear Function
Sigmoid
Tanh
ReLU
Leaky ReLU
ELU
Softmax
```

---

# 1. Step Function

## Theory

The simplest activation function.

---

Formula:

```text
Output = 1

if x ≥ 0

Output = 0

if x < 0
```

---

Example:

Input:

```text
5
```

Output:

```text
1
```

---

Input:

```text
-3
```

Output:

```text
0
```

---

Visualization

```text
1 ──────
        │
        │
0 ──────└────────
        0
```

---

# Advantages

```text
Simple
Easy to Understand
```

---

# Disadvantages

```text
Not Differentiable
No Gradient Information
Not Used in Deep Learning
```

---

# 2. Linear Activation

## Theory

Output equals input.

Formula:

```text
f(x) = x
```

---

Example:

```text
Input = 10

Output = 10
```

---

Visualization

```text
      /
     /
    /
   /
```

---

# Problem

Using only linear activations:

```text
Deep Network
=
Linear Model
```

---

Therefore:

```text
Rarely Used
```

---

# 3. Sigmoid Function

## Theory

Most popular activation in early Neural Networks.

---

Formula:

```text
        1
----------------
1 + e^(-x)
```

---

Output Range:

```text
0 to 1
```

---

Example

Input:

```text
0
```

Output:

```text
0.5
```

---

Input:

```text
Large Positive Number
```

Output:

```text
≈ 1
```

---

Input:

```text
Large Negative Number
```

Output:

```text
≈ 0
```

---

Visualization

```text
     ______
   /
 /
/
 \______
```

---

# Advantages

```text
Probability Output
Easy Interpretation
```

---

# Disadvantages

```text
Vanishing Gradient Problem
Slow Training
```

---

# Use Cases

```text
Binary Classification Output Layer
```

---

# Python Example

```python
import numpy as np

x = 2

sigmoid = (
    1 /
    (1 + np.exp(-x))
)

print(sigmoid)
```

---

# 4. Tanh (Hyperbolic Tangent)

## Theory

Improved version of Sigmoid.

---

Formula:

```text
tanh(x)
```

---

Output Range:

```text
-1 to 1
```

---

Example:

```text
Input = 0

Output = 0
```

---

Visualization

```text
      ______
    /
---/
  /
 /
------
```

---

# Advantages

```text
Zero-Centered
Better Than Sigmoid
```

---

# Disadvantages

```text
Still Suffers From Vanishing Gradient
```

---

# Use Cases

```text
Hidden Layers (Older Networks)
RNNs
LSTMs
```

---

# 5. ReLU (Rectified Linear Unit)

## Theory

Most widely used activation function today.

---

Formula:

```text
f(x)

=

max(0,x)
```

---

Examples

Input:

```text
-5
```

Output:

```text
0
```

---

Input:

```text
8
```

Output:

```text
8
```

---

Visualization

```text
     /
    /
___/
```

---

# Advantages

```text
Fast
Simple
Computationally Efficient
Reduces Vanishing Gradient
```

---

# Disadvantages

```text
Dead Neuron Problem
```

---

# Use Cases

```text
CNNs
Deep Neural Networks
Transformers
LLMs
```

---

# Python Example

```python
import numpy as np

x = -5

relu = max(0, x)

print(relu)
```

---

# 6. Leaky ReLU

## Theory

Improved version of ReLU.

---

Problem with ReLU:

```text
Negative Values Become Zero
```

---

Solution:

Allow a small negative slope.

---

Formula:

```text
x

if x > 0

0.01x

if x ≤ 0
```

---

Example

Input:

```text
-10
```

Output:

```text
-0.1
```

---

Visualization

```text
    /
   /
__/
 /
```

---

# Advantages

```text
Reduces Dead Neurons
Better Gradient Flow
```

---

# Use Cases

```text
Deep Networks
CNNs
```

---

# 7. ELU

## Exponential Linear Unit

Formula:

```text
x

if x > 0

α(e^x - 1)

if x < 0
```

---

Advantages:

```text
Faster Convergence
Reduces Bias Shift
```

---

# 8. Softmax

## Theory

Used in Multi-Class Classification.

---

Converts outputs into probabilities.

---

Example

Before Softmax:

```text
Cat = 2.1

Dog = 1.5

Bird = 0.3
```

---

After Softmax:

```text
Cat = 0.65

Dog = 0.25

Bird = 0.10
```

---

Total:

```text
1.0
```

---

# Advantages

```text
Probability Distribution
Perfect For Multi-Class Problems
```

---

# Use Cases

```text
Image Classification
Language Models
NLP
```

---

# Activation Function Comparison

| Function | Range | Use Case |
|-----------|--------|-----------|
| Step | 0,1 | Perceptrons |
| Linear | (-∞,+∞) | Regression Output |
| Sigmoid | 0 to 1 | Binary Classification |
| Tanh | -1 to 1 | Hidden Layers |
| ReLU | 0 to ∞ | Deep Learning |
| Leaky ReLU | (-∞,+∞) | Deep Networks |
| ELU | (-∞,+∞) | Deep Learning |
| Softmax | 0 to 1 | Multi-Class Classification |

---

# Vanishing Gradient Problem

## Theory

Gradients become extremely small during backpropagation.

---

Occurs in:

```text
Sigmoid
Tanh
```

---

Effects:

```text
Slow Learning
Poor Training
```

---

Solution:

```text
ReLU
Leaky ReLU
```

---

# Choosing Activation Functions

## Hidden Layers

Most common:

```text
ReLU
Leaky ReLU
```

---

## Binary Classification Output

```text
Sigmoid
```

---

## Multi-Class Classification Output

```text
Softmax
```

---

## Regression Output

```text
Linear Activation
```

---

# Neural Network Example

Fraud Detection:

Features:

```text
Claim Amount

Vehicle Age

Policy Age
```

---

Network:

```text
Input
  ↓
ReLU
  ↓
ReLU
  ↓
Sigmoid
```

---

Output:

```text
Fraud Probability
```

---

# TensorFlow Example

```python
from tensorflow.keras.layers import Dense

Dense(
    128,
    activation="relu"
)

Dense(
    1,
    activation="sigmoid"
)
```

---

# Interview Questions

### Q1. What is an Activation Function?

```text
A function that introduces non-linearity into a neural network.
```

---

### Q2. Why are Activation Functions needed?

```text
Without them, neural networks behave like linear models.
```

---

### Q3. Why is ReLU popular?

```text
Fast computation and reduced vanishing gradient issues.
```

---

### Q4. When do we use Sigmoid?

```text
Binary Classification Output Layer.
```

---

### Q5. When do we use Softmax?

```text
Multi-Class Classification Output Layer.
```

---

# Learning Path

```text
Step Function
      ↓
Linear Activation
      ↓
Sigmoid
      ↓
Tanh
      ↓
ReLU
      ↓
Leaky ReLU
      ↓
Softmax
      ↓
Deep Learning Architectures
```

# Most Important Activation Functions for AI Engineers

```text
Sigmoid
Tanh
ReLU
Leaky ReLU
Softmax
```

These activation functions are used extensively in:

```text
Neural Networks
CNNs
RNNs
LSTMs
Transformers
Large Language Models (LLMs)
Computer Vision
Generative AI
```

Modern architectures such as Transformers and LLMs primarily rely on variants of:

```text
ReLU
GELU
Softmax
```

for efficient learning and high-performance training.