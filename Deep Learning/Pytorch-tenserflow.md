# PyTorch

## What is PyTorch?

PyTorch is an open-source Deep Learning framework developed by:

:contentReference[oaicite:0]{index=0}

It is one of the most widely used frameworks for:

```text
Deep Learning
Machine Learning
Computer Vision
Natural Language Processing
Generative AI
Large Language Models
```

---

# Why PyTorch?

PyTorch provides:

```text
Easy Development
Dynamic Computation Graphs
GPU Support
Research Flexibility
Production Deployment
```

---

# Applications

```text
CNNs
RNNs
LSTMs
Transformers
LLMs
Computer Vision
Speech Recognition
```

---

# PyTorch Architecture

```text
Data
  ↓
Tensor
  ↓
Neural Network
  ↓
Loss Function
  ↓
Optimizer
  ↓
Training
```

---

# What is a Tensor?

A Tensor is the fundamental data structure in PyTorch.

Think of a Tensor as:

```text
Advanced NumPy Array
```

---

Examples

## Scalar (0D Tensor)

```python
import torch

x = torch.tensor(5)
```

---

## Vector (1D Tensor)

```python
x = torch.tensor(
    [1,2,3]
)
```

---

## Matrix (2D Tensor)

```python
x = torch.tensor(
    [
        [1,2],
        [3,4]
    ]
)
```

---

# Tensor Operations

```python
import torch

a = torch.tensor([1,2,3])

b = torch.tensor([4,5,6])

print(a + b)
```

Output:

```text
tensor([5,7,9])
```

---

# Automatic Differentiation

## Autograd

PyTorch automatically computes gradients.

---

Example

```python
x = torch.tensor(
    2.0,
    requires_grad=True
)

y = x ** 2

y.backward()

print(
    x.grad
)
```

Output:

```text
4
```

---

# Building Neural Networks

PyTorch provides:

```text
torch.nn
```

module.

---

Example

```python
import torch.nn as nn

model = nn.Linear(
    10,
    1
)
```

---

# Simple Neural Network

```python
import torch.nn as nn

model = nn.Sequential(

    nn.Linear(10,64),

    nn.ReLU(),

    nn.Linear(64,1)
)
```

---

# Loss Functions

Common losses:

```text
MSELoss
CrossEntropyLoss
BCELoss
```

---

Example

```python
criterion = nn.MSELoss()
```

---

# Optimizers

PyTorch provides:

```text
SGD
Adam
AdamW
RMSProp
```

---

Example

```python
optimizer = torch.optim.Adam(
    model.parameters(),
    lr=0.001
)
```

---

# Training Loop

```python
for epoch in range(100):

    optimizer.zero_grad()

    output = model(X)

    loss = criterion(
        output,
        y
    )

    loss.backward()

    optimizer.step()
```

---

# GPU Support

PyTorch can use GPUs.

Example:

```python
device = "cuda"

model.to(device)
```

---

Benefits:

```text
Faster Training
Large Models
LLM Training
```

---

# PyTorch Ecosystem

Popular Libraries:

```text
TorchVision
TorchText
TorchAudio
PyTorch Lightning
Hugging Face Transformers
```

---

# Real-World Usage

Used heavily in:

```text
Research
LLMs
Computer Vision
Multimodal AI
Generative AI
```

---

# TensorFlow

## What is TensorFlow?

TensorFlow is an open-source Deep Learning framework developed by:

:contentReference[oaicite:1]{index=1}

---

# Why TensorFlow?

TensorFlow is designed for:

```text
Training
Deployment
Production AI Systems
Mobile AI
Cloud AI
```

---

# Applications

```text
Machine Learning
Deep Learning
Computer Vision
NLP
Recommendation Systems
Generative AI
```

---

# TensorFlow Architecture

```text
Data
  ↓
Tensor
  ↓
Model
  ↓
Loss
  ↓
Optimizer
  ↓
Training
```

---

# Tensor

TensorFlow also uses:

```text
Tensors
```

as the primary data structure.

---

Example

```python
import tensorflow as tf

x = tf.constant(
    [1,2,3]
)
```

---

# Tensor Operations

```python
a = tf.constant([1,2])

b = tf.constant([3,4])

print(a + b)
```

Output:

```text
[4,6]
```

---

# Keras API

Most TensorFlow projects use:

```text
Keras
```

---

Benefits:

```text
Easy Development
Less Code
Production Ready
```

---

# Building Neural Networks

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
```

---

# Simple Neural Network

```python
model = Sequential()

model.add(
    Dense(
        64,
        activation="relu"
    )
)

model.add(
    Dense(
        1
    )
)
```

---

# Compile Model

```python
model.compile(

    optimizer="adam",

    loss="mse",

    metrics=["accuracy"]
)
```

---

# Train Model

```python
model.fit(

    X_train,

    y_train,

    epochs=10
)
```

---

# Evaluate Model

```python
model.evaluate(
    X_test,
    y_test
)
```

---

# TensorFlow Ecosystem

Popular Components:

```text
Keras
TensorBoard
TensorFlow Lite
TensorFlow Serving
TFX
```

---

# TensorBoard

Used for:

```text
Visualization
Monitoring
Training Analysis
```

---

# TensorFlow Lite

Used for:

```text
Mobile Applications
Edge AI
IoT
```

---

# TensorFlow Serving

Used for:

```text
Model Deployment
Production Inference
```

---

# TensorFlow Extended (TFX)

Used for:

```text
MLOps
Production Pipelines
```

---

# PyTorch vs TensorFlow

| Feature | PyTorch | TensorFlow |
|----------|----------|----------|
| Ease of Learning | Excellent | Good |
| Research | Excellent | Good |
| Production | Good | Excellent |
| Debugging | Easier | Moderate |
| Flexibility | High | Medium |
| Deployment | Good | Excellent |

---

# When to Use PyTorch?

Choose PyTorch for:

```text
Research
Experimentation
LLM Development
Computer Vision
Academic Projects
```

---

# When to Use TensorFlow?

Choose TensorFlow for:

```text
Production Systems
Mobile Apps
Enterprise AI
MLOps Pipelines
Edge AI
```

---

# Insurance Example

## Claim Severity Prediction

Using PyTorch:

```text
Claims Dataset
      ↓
Neural Network
      ↓
Severity Prediction
```

---

Using TensorFlow:

```text
Claims Dataset
      ↓
Model Training
      ↓
TensorFlow Serving
      ↓
Production Deployment
```

---

# Modern AI Landscape

Many modern models are built using PyTorch:

```text
Transformers
LLMs
Generative AI Models
```

Examples include models from organizations such as:

- :contentReference[oaicite:2]{index=2}
- :contentReference[oaicite:3]{index=3}
- :contentReference[oaicite:4]{index=4}

---

# Interview Questions

### Q1. What is PyTorch?

```text
An open-source deep learning framework known for flexibility and research-friendly development.
```

---

### Q2. What is TensorFlow?

```text
An open-source deep learning framework focused on scalable training and production deployment.
```

---

### Q3. What is a Tensor?

```text
A multidimensional data structure used to store and process numerical data.
```

---

### Q4. What is Autograd in PyTorch?

```text
A system that automatically computes gradients for backpropagation.
```

---

### Q5. What is Keras?

```text
A high-level API used to build and train TensorFlow models.
```

---

# Learning Path

```text
Tensors
    ↓
Tensor Operations
    ↓
Neural Networks
    ↓
Loss Functions
    ↓
Optimizers
    ↓
Training Loops
    ↓
CNNs
    ↓
RNNs
    ↓
Transformers
    ↓
LLMs
```

# Most Important Topics for AI Engineers

```text
Tensors
Autograd
Neural Networks
Loss Functions
Optimizers
Training Loops
GPU Computing
Keras
TensorBoard
Model Deployment
```

Both PyTorch and TensorFlow are industry-standard frameworks used for:

```text
Deep Learning
Computer Vision
NLP
Generative AI
Large Language Models
MLOps
AI Engineering
```

For AI Engineers today:

```text
PyTorch → Most Important for Research and LLMs

TensorFlow → Most Important for Production and Enterprise AI
```