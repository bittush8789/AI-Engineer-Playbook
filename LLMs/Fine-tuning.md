# Fine-Tuning

## What is Fine-Tuning?

Fine-Tuning is the process of taking a pre-trained Large Language Model (LLM) and training it further on a specific dataset to make it better at a particular task or domain.

---

# Why Fine-Tune?

Base LLM:

```text
General Knowledge
```

---

Fine-Tuned LLM:

```text
Domain Knowledge
Task Specialization
Custom Behavior
```

---

# Example

Base Model:

```text
General Chatbot
```

---

Fine-Tuned Model:

```text
Insurance Claims Assistant
Medical Assistant
Legal Assistant
Code Assistant
```

---

# Real-World Example

Suppose we have:

```text
Llama 3
```

---

Train it on:

```text
10,000 Insurance Claims
```

---

Result:

```text
Insurance Expert Model
```

---

# Fine-Tuning Workflow

```text
Pretrained Model
       ↓
Domain Dataset
       ↓
Training
       ↓
Updated Weights
       ↓
Specialized Model
```

---

# Types of Fine-Tuning

```text
Full Fine-Tuning
Parameter Efficient Fine-Tuning (PEFT)
Instruction Fine-Tuning
Supervised Fine-Tuning (SFT)
```

---

# Full Fine-Tuning

## Theory

Update all model parameters.

---

Example:

```text
7 Billion Parameters
```

All updated.

---

Advantages:

```text
Highest Flexibility
Best Adaptation
```

---

Disadvantages:

```text
Very Expensive
Requires GPUs
Large Storage
```

---

# Example

Model:

```text
7B Parameters
```

Training:

```text
All 7B Updated
```

---

# Supervised Fine-Tuning (SFT)

## Theory

Train model on:

```text
Input → Output Pairs
```

---

Example

Dataset:

```text
Question:
What is AI?

Answer:
Artificial Intelligence...
```

---

Goal:

```text
Learn Desired Responses
```

---

# Instruction Fine-Tuning

## Theory

Train model to follow instructions better.

---

Example

```text
Summarize This Article

Translate To French

Generate Python Code
```

---

Result:

```text
Better Instruction Following
```

---

# Challenges of Full Fine-Tuning

```text
High GPU Cost
Long Training Time
Large Storage
High Memory Usage
```

---

# PEFT (Parameter Efficient Fine-Tuning)

## What is PEFT?

PEFT stands for:

```text
Parameter Efficient Fine-Tuning
```

---

Instead of updating:

```text
Entire Model
```

update:

```text
Small Subset Of Parameters
```

---

Benefits:

```text
Lower Cost
Faster Training
Less Memory
Easy Deployment
```

---

# Example

Full Model:

```text
7 Billion Parameters
```

---

PEFT Updates:

```text
1-2 Million Parameters
```

---

# Popular PEFT Methods

```text
LoRA
QLoRA
Prefix Tuning
Prompt Tuning
Adapters
```

---

# LoRA

## What is LoRA?

LoRA stands for:

```text
Low-Rank Adaptation
```

Introduced to fine-tune LLMs efficiently.

---

# Core Idea

Instead of modifying original weights:

```text
Freeze Original Model
```

and train:

```text
Small Adapter Matrices
```

---

Visualization

```text
Base Model
     ↓
Frozen Weights
     ↓
LoRA Adapters
     ↓
Task Learning
```

---

# Why LoRA?

Traditional Fine-Tuning:

```text
Huge GPU Memory
```

---

LoRA:

```text
Much Smaller Memory
```

---

# Example

Full Fine-Tuning:

```text
7B Parameters
```

---

LoRA:

```text
Only Few Million Parameters
```

trained.

---

# Benefits

```text
Cheap
Fast
Memory Efficient
Widely Used
```

---

# LoRA Hyperparameters

Important Parameters:

```text
Rank (r)
Alpha
Dropout
```

---

# Rank (r)

Controls:

```text
Adapter Size
```

---

Typical Values:

```text
4
8
16
32
64
```

---

# LoRA Workflow

```text
Pretrained Model
       ↓
Freeze Weights
       ↓
Insert LoRA Layers
       ↓
Train Adapters
       ↓
Specialized Model
```

---

# QLoRA

## What is QLoRA?

QLoRA stands for:

```text
Quantized Low-Rank Adaptation
```

---

Introduced in 2023.

---

# Goal

Combine:

```text
Quantization
+
LoRA
```

---

Benefits:

```text
Train Large Models
Using Small GPUs
```

---

# How QLoRA Works

Step 1

```text
Quantize Model
```

---

Step 2

```text
Apply LoRA Adapters
```

---

Step 3

```text
Train Adapters
```

---

# Example

Model:

```text
Llama 2 70B
```

---

Traditional Fine-Tuning:

```text
Multiple High-End GPUs
```

---

QLoRA:

```text
Single GPU Possible
```

---

# Why QLoRA Became Popular?

Advantages:

```text
Very Low Memory
Very Low Cost
High Performance
```

---

# LoRA vs QLoRA

| LoRA | QLoRA |
|--------|--------|
| Standard Model | Quantized Model |
| Lower Memory | Much Lower Memory |
| Faster | Slightly Slower |
| Popular | Extremely Popular |

---

# Model Quantization

## What is Quantization?

Quantization reduces model size by storing weights with fewer bits.

---

Example

Standard:

```text
FP32
```

32-bit floating point.

---

Quantized:

```text
INT8
INT4
```

---

# Why Quantization?

Benefits:

```text
Smaller Models
Faster Inference
Lower Cost
Less RAM Usage
```

---

# Example

Model:

```text
7GB
```

---

INT8:

```text
≈ 3.5GB
```

---

INT4:

```text
≈ 1.75GB
```

---

# Quantization Types

```text
FP16
BF16
INT8
INT4
GPTQ
AWQ
GGUF
```

---

# FP16

Half Precision.

---

Benefits:

```text
Faster Training
Less Memory
```

---

# INT8 Quantization

Uses:

```text
8 Bits
```

instead of:

```text
32 Bits
```

---

Memory Reduction:

```text
~75%
```

---

# INT4 Quantization

Uses:

```text
4 Bits
```

---

Benefits:

```text
Very Small Models
```

---

Used heavily in:

```text
Ollama
Local LLMs
Edge AI
```

---

# GPTQ

Popular post-training quantization technique.

---

Benefits:

```text
Fast Inference
Good Accuracy
```

---

# AWQ

Stands for:

```text
Activation-Aware Weight Quantization
```

---

Widely used for:

```text
Production LLM Serving
```

---

# GGUF

Popular format used by:

:contentReference[oaicite:0]{index=0}

and:

:contentReference[oaicite:1]{index=1}

---

Benefits:

```text
Local Inference
CPU Inference
Edge Devices
```

---

# Fine-Tuning vs RAG

| Fine-Tuning | RAG |
|------------|------------|
| Updates Model | Uses External Knowledge |
| Expensive | Cheaper |
| Permanent Knowledge | Dynamic Knowledge |
| Retraining Required | No Retraining |

---

# When to Use Fine-Tuning?

Use for:

```text
Custom Writing Style
Domain Adaptation
Instruction Following
Task Specialization
```

---

# When to Use RAG?

Use for:

```text
Company Documents
Knowledge Bases
Dynamic Information
Frequently Updated Data
```

---

# Insurance Example

Train Model On:

```text
FNOL Data
Claims Notes
Policy Documents
Coverage Rules
```

---

Result:

```text
Insurance Claims Assistant
```

---

# Hugging Face Example

Popular Libraries:

- :contentReference[oaicite:2]{index=2}
- :contentReference[oaicite:3]{index=3}
- :contentReference[oaicite:4]{index=4}

---

# Interview Questions

### Q1. What is Fine-Tuning?

```text
Training a pre-trained model on a task-specific dataset.
```

---

### Q2. What is PEFT?

```text
Parameter Efficient Fine-Tuning that updates only a small subset of parameters.
```

---

### Q3. What is LoRA?

```text
A PEFT technique that freezes the base model and trains low-rank adapter matrices.
```

---

### Q4. What is QLoRA?

```text
A combination of quantization and LoRA that enables efficient fine-tuning of large models.
```

---

### Q5. What is Quantization?

```text
Reducing model precision to decrease memory usage and increase inference speed.
```

---

# Learning Path

```text
LLM Fundamentals
      ↓
Fine-Tuning
      ↓
SFT
      ↓
PEFT
      ↓
LoRA
      ↓
QLoRA
      ↓
Quantization
      ↓
RAG
      ↓
RLHF
      ↓
Advanced LLM Training
```

# Most Important Topics for AI Engineers

```text
Fine-Tuning
SFT
Instruction Tuning
PEFT
LoRA
QLoRA
FP16
INT8
INT4
GPTQ
AWQ
GGUF
```

These techniques are heavily used in:

```text
LLM Customization
Domain-Specific Assistants
RAG Systems
Agentic AI
Local LLM Deployment
Enterprise AI Platforms
AI Infrastructure
LLMOps
```

For modern AI Engineers, **LoRA, QLoRA, PEFT, and Quantization** are among the most practical and widely used techniques for adapting and deploying large language models efficiently.