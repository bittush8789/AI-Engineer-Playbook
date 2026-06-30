# Foundation Models

## What are Foundation Models?

Foundation Models are large pre-trained AI models trained on massive datasets that can be adapted to many downstream tasks.

They serve as the foundation for:

```text
Chatbots
RAG Systems
AI Agents
Code Assistants
Search Systems
Multimodal AI
```

---

# Why Called Foundation Models?

Because one model can perform multiple tasks:

```text
Text Generation
Question Answering
Translation
Summarization
Reasoning
Coding
Image Understanding
```

without training separate models.

---

# Traditional AI

```text
One Model
      ↓
One Task
```

Example:

```text
Spam Detection Model
```

---

# Foundation Models

```text
One Large Model
        ↓
Many Tasks
```

---

# Examples

- GPT
- Gemini
- Claude
- Llama
- Mistral

---

# Characteristics of Foundation Models

```text
Large Scale Training
Billions of Parameters
General Purpose
Transfer Learning
Instruction Following
Few-Shot Learning
```

---

# Foundation Model Workflow

```text
Massive Dataset
       ↓
Pretraining
       ↓
Foundation Model
       ↓
Fine-Tuning / RAG
       ↓
AI Application
```

---

# GPT Models

## What is GPT?

GPT stands for:

```text
Generative Pre-trained Transformer
```

Developed by:

:contentReference[oaicite:5]{index=5}

---

# GPT Architecture

Uses:

```text
Decoder-Only Transformer
```

---

Workflow:

```text
Prompt
   ↓
Transformer Layers
   ↓
Next Token Prediction
   ↓
Response
```

---

# Evolution of GPT

## GPT-1

Released:

```text
2018
```

Parameters:

```text
117 Million
```

---

## GPT-2

Released:

```text
2019
```

Parameters:

```text
1.5 Billion
```

---

Major breakthrough:

```text
Text Generation
```

---

## GPT-3

Released:

```text
2020
```

Parameters:

```text
175 Billion
```

---

Capabilities:

```text
Writing
Coding
Reasoning
Translation
```

---

## GPT-4

Major improvements:

```text
Reasoning
Accuracy
Multimodal Capability
```

---

# Strengths of GPT Models

```text
Excellent Reasoning
Coding
Agent Workflows
Tool Calling
Content Generation
```

---

# Applications

```text
Chatbots
Code Generation
AI Agents
RAG Systems
Copilots
```

---

# Gemini Models

## What is Gemini?

Gemini is Google's flagship AI model family.

Developed by:

:contentReference[oaicite:6]{index=6}

---

# Goal

Create:

```text
Native Multimodal AI
```

---

# What is Multimodal?

Ability to understand:

```text
Text
Images
Audio
Video
Documents
Code
```

simultaneously.

---

# Gemini Architecture

Built around Transformer-based architectures optimized for multimodal understanding.

---

# Gemini Capabilities

```text
Reasoning
Coding
Image Understanding
Video Analysis
Document Processing
```

---

# Example

Input:

```text
Image
+
Question
```

---

Output:

```text
Explanation
```

---

# Gemini Strengths

```text
Long Context Windows
Multimodal Processing
Search Integration
Document Understanding
```

---

# Applications

```text
Document AI
Enterprise Search
Code Assistance
Research
Knowledge Systems
```

---

# Claude Models

## What is Claude?

Claude is a family of AI models developed by:

:contentReference[oaicite:7]{index=7}

---

Named after:

:contentReference[oaicite:8]{index=8}

---

# Design Philosophy

Focus on:

```text
Safety
Reliability
Alignment
Reasoning
```

---

# Claude Architecture

Based on advanced Transformer architectures.

---

# Strengths

```text
Long Context Handling
Document Analysis
Reasoning
Writing
Enterprise Use Cases
```

---

# Claude Features

```text
Large Context Windows
Strong Summarization
Knowledge Extraction
Long Document Analysis
```

---

# Example

Input:

```text
Large PDF
```

---

Output:

```text
Summary
Insights
Action Items
```

---

# Applications

```text
Knowledge Management
Research
Document Processing
Enterprise AI
RAG Systems
```

---

# GPT vs Gemini vs Claude

| Feature | GPT | Gemini | Claude |
|----------|----------|----------|----------|
| Coding | Excellent | Excellent | Very Good |
| Reasoning | Excellent | Excellent | Excellent |
| Long Context | Very Good | Excellent | Excellent |
| Multimodal | Excellent | Excellent | Very Good |
| Enterprise Docs | Very Good | Excellent | Excellent |
| AI Agents | Excellent | Excellent | Very Good |

---

# Open Source LLMs

## What are Open Source LLMs?

LLMs whose weights or usage are publicly available for research, customization, or self-hosting.

---

# Why Open Source?

Benefits:

```text
Lower Cost
Customization
Privacy
Self Hosting
Fine-Tuning
```

---

# Popular Open Source Models

```text
Llama
Mistral
Mixtral
Qwen
DeepSeek
Phi
Gemma
Falcon
```

---

# 1. Llama

Developed by:

:contentReference[oaicite:9]{index=9}

---

Most popular open-source LLM family.

---

Strengths:

```text
Fine-Tuning
RAG
Agent Systems
Research
```

---

Common Sizes:

```text
8B
70B
405B
```

---

# 2. Mistral

Developed by:

:contentReference[oaicite:10]{index=10}

---

Known for:

```text
Efficiency
Strong Performance
Lower Hardware Requirements
```

---

# 3. Mixtral

Mixture-of-Experts (MoE) model.

---

Benefits:

```text
High Performance
Efficient Inference
```

---

# 4. Qwen

Developed by:

:contentReference[oaicite:11]{index=11}

---

Strengths:

```text
Coding
Reasoning
Multilingual Support
```

---

# 5. DeepSeek

Developed by:

:contentReference[oaicite:12]{index=12}

---

Popular for:

```text
Coding
Reasoning
Low Cost Deployment
```

---

# 6. Gemma

Developed by:

:contentReference[oaicite:13]{index=13}

---

Open-weight model family.

---

Benefits:

```text
Research
Fine-Tuning
Local Deployment
```

---

# Open Source LLM Workflow

```text
Model Download
      ↓
Quantization
      ↓
Fine-Tuning
      ↓
RAG Integration
      ↓
Deployment
```

---

# Why AI Engineers Use Open Source Models

```text
Custom Fine-Tuning
Private Data
On-Prem Deployment
Cost Reduction
Experimentation
```

---

# Insurance Example

Train:

```text
Llama 3
```

on:

```text
Claims Notes
FNOL Data
Coverage Rules
```

---

Result:

```text
Insurance Assistant
```

---

Deploy using:

```text
vLLM
KServe
Ollama
```

---

# Choosing the Right Model

## GPT

Best For:

```text
General AI Applications
Agents
Coding
Reasoning
```

---

## Gemini

Best For:

```text
Multimodal Systems
Document Processing
Search
```

---

## Claude

Best For:

```text
Long Documents
Research
Enterprise Knowledge Systems
```

---

## Open Source LLMs

Best For:

```text
Customization
Private Deployment
Fine-Tuning
Cost Optimization
```

---

# Interview Questions

### Q1. What is a Foundation Model?

```text
A large pre-trained model that can be adapted to many downstream tasks.
```

---

### Q2. What does GPT stand for?

```text
Generative Pre-trained Transformer.
```

---

### Q3. What makes Gemini unique?

```text
Strong native multimodal capabilities.
```

---

### Q4. What is Claude known for?

```text
Long-context reasoning, document analysis, and AI safety.
```

---

### Q5. Why use Open Source LLMs?

```text
Customization, privacy, fine-tuning, and lower deployment costs.
```

---

