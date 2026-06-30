# Word2Vec

## What is Word2Vec?

Word2Vec is a neural network-based algorithm used to learn word embeddings from large text corpora.

Developed by:

:contentReference[oaicite:0]{index=0} (2013)

---

# Goal

Convert words into dense numerical vectors.

```text
dog
```

↓

```text
[0.23, 0.81, 0.15]
```

---

# Main Architectures

## CBOW

```text
Context Words
      ↓
Predict Target Word
```

Example:

```text
I love ___ Learning
```

↓

```text
Machine
```

---

## Skip-Gram

```text
Target Word
      ↓
Predict Context Words
```

Example:

```text
Machine
```

↓

```text
I
love
Learning
```

---

# Advantages

```text
Fast
Efficient
Captures Semantics
```

---

# Limitation

Same word always gets same embedding.

Example:

```text
Bank
```

```text
River Bank
Financial Bank
```

Same vector.

---

# FastText

## What is FastText?

FastText is an improved version of Word2Vec developed by:

:contentReference[oaicite:1]{index=1}

---

# Problem with Word2Vec

Unknown words cannot be handled well.

Example:

```text
ChatGPT
```

May not exist during training.

---

# FastText Solution

Break words into character n-grams.

Example:

```text
playing
```

↓

```text
pla
lay
ayi
yin
ing
```

---

Instead of learning:

```text
playing
```

FastText learns:

```text
Subwords
```

---

# Advantages

```text
Handles Rare Words
Handles Misspellings
Better Generalization
```

---

# Example

Word:

```text
insurance
```

Subwords:

```text
ins
sur
ura
ran
anc
nce
```

---

# Applications

```text
Search Engines
Spell Correction
Text Classification
Chatbots
```

---

# FastText vs Word2Vec

| Word2Vec | FastText |
|-----------|-----------|
| Word Level | Subword Level |
| Poor for Rare Words | Excellent |
| Smaller Model | Larger Model |
| Faster | Slightly Slower |

---

# GloVe

## What is GloVe?

GloVe stands for:

```text
Global Vectors for Word Representation
```

Developed by:

:contentReference[oaicite:2]{index=2}

---

# Goal

Learn word embeddings using:

```text
Global Word Statistics
```

instead of only local context.

---

# Example

Words:

```text
King

Queen

Man

Woman
```

---

Embeddings learn:

```text
King - Man + Woman

≈

Queen
```

---

# How GloVe Works

Uses:

```text
Word Co-occurrence Matrix
```

---

Example

Sentence:

```text
The cat sits on the mat.
```

---

Records:

```text
cat appears near sits

cat appears near mat
```

---

Builds statistical relationships.

---

# Advantages

```text
Captures Global Context
High Quality Embeddings
Efficient
```

---

# Limitation

Still produces:

```text
Static Embeddings
```

---

# Word2Vec vs GloVe

| Word2Vec | GloVe |
|-----------|-----------|
| Local Context | Global Context |
| Predictive Model | Statistical Model |
| Neural Network | Matrix Factorization |
| Fast | Accurate |

---

# Seq2Seq Models

## What is Seq2Seq?

Seq2Seq stands for:

```text
Sequence-to-Sequence
```

A Neural Network architecture that converts one sequence into another.

---

# Examples

```text
Translation

English → French

Summarization

Long Text → Summary

Question Answering

Question → Answer
```

---

# Architecture

Contains:

```text
Encoder
Decoder
```

---

Visualization

```text
Input Sequence
        ↓
Encoder
        ↓
Context Vector
        ↓
Decoder
        ↓
Output Sequence
```

---

# Example

Input:

```text
I love AI
```

---

Output:

```text
J'aime l'IA
```

---

# Encoder

Purpose:

```text
Understand Input
```

---

# Decoder

Purpose:

```text
Generate Output
```

---

# Problem

Long sentences cause:

```text
Information Loss
```

because everything is compressed into a single vector.

---

# Attention Mechanism

## What is Attention?

Attention allows the model to focus on important words while generating output.

---

Before Attention

```text
Entire Sentence
      ↓
Single Context Vector
```

---

After Attention

```text
Focus On Important Words
```

---

# Example

Translation:

```text
The cat sits on the mat
```

While generating:

```text
cat
```

Attention focuses on:

```text
cat
```

instead of the entire sentence.

---

# Why Attention?

Benefits:

```text
Better Long-Range Understanding
Higher Accuracy
Improved Translation
```

---

# Attention Formula

Core idea:

```text
Query

Key

Value
```

---

Attention computes:

```text
Relevant Information
```

from the input sequence.

---

# Self-Attention

## Theory

Words attend to other words in the same sentence.

---

Example

Sentence:

```text
The animal didn't cross the street because it was tired.
```

---

Word:

```text
it
```

attends to:

```text
animal
```

---

Allows understanding context.

---

# Transformers

## What are Transformers?

Transformers are Deep Learning architectures built entirely on Attention mechanisms.

Introduced in the landmark paper:

```text
Attention Is All You Need
```

(2017)

---

# Why Transformers?

RNNs and LSTMs suffer from:

```text
Sequential Processing
Slow Training
Limited Long-Term Memory
```

---

Transformers solve these issues.

---

# Transformer Architecture

```text
Input
  ↓
Embedding
  ↓
Positional Encoding
  ↓
Multi-Head Attention
  ↓
Feed Forward Network
  ↓
Output
```

---

# Core Components

```text
Embeddings
Positional Encoding
Self-Attention
Multi-Head Attention
Feed Forward Networks
```

---

# Positional Encoding

Transformers process tokens in parallel.

Need to know:

```text
Word Order
```

---

Solution:

```text
Positional Encoding
```

---

Example

```text
I love AI
```

Different from:

```text
AI love I
```

---

# Multi-Head Attention

Instead of one attention mechanism:

```text
Multiple Attention Heads
```

---

Benefits:

```text
Capture Multiple Relationships
Better Understanding
```

---

# Transformer Workflow

```text
Text
 ↓
Tokenization
 ↓
Embeddings
 ↓
Self-Attention
 ↓
Transformer Layers
 ↓
Prediction
```

---

# Transformer Variants

## Encoder-Only

Examples:

```text
BERT
RoBERTa
DeBERTa
```

Used for:

```text
Classification
NER
Search
```

---

## Decoder-Only

Examples:

```text
GPT
Llama
Claude
```

Used for:

```text
Text Generation
Chatbots
LLMs
```

---

## Encoder-Decoder

Examples:

```text
T5
BART
FLAN-T5
```

Used for:

```text
Translation
Summarization
Question Answering
```

---

# Why Transformers Dominated AI

Advantages:

```text
Parallel Training
Long Context Handling
Scalability
High Accuracy
```

---

# Applications

```text
LLMs
Chatbots
Translation
Search Engines
RAG Systems
Code Generation
Agentic AI
```

---

# Insurance Example

Claim Note:

```text
Vehicle suffered major collision damage.
```

---

Transformer learns:

```text
vehicle
collision
damage
```

relationships simultaneously.

---

Applications:

```text
Claim Classification
Fraud Detection
FNOL Routing
Document Understanding
```

---

# Evolution of NLP

```text
Bag of Words
      ↓
TF-IDF
      ↓
Word2Vec
      ↓
FastText
      ↓
GloVe
      ↓
RNN
      ↓
LSTM
      ↓
Seq2Seq
      ↓
Attention
      ↓
Transformers
      ↓
LLMs
```

---

# Interview Questions

### Q1. What is Word2Vec?

```text
A neural network-based algorithm used to learn word embeddings.
```

---

### Q2. How is FastText different from Word2Vec?

```text
FastText uses subword information, while Word2Vec uses complete words.
```

---

### Q3. What is GloVe?

```text
A word embedding technique based on global word co-occurrence statistics.
```

---

### Q4. What problem does Attention solve?

```text
It allows models to focus on relevant parts of the input instead of compressing everything into one vector.
```

---

### Q5. Why are Transformers better than RNNs?

```text
Parallel processing, better long-range dependency handling, and higher scalability.
```

---

# Most Important Topics for AI Engineers

```text
Word2Vec
CBOW
Skip-Gram
FastText
GloVe
Seq2Seq
Encoder-Decoder
Attention
Self-Attention
Multi-Head Attention
Transformers
Positional Encoding
```

These concepts form the direct foundation of:

```text
BERT
GPT
Llama
Claude
Gemini
RAG Systems
Agentic AI
Large Language Models (LLMs)
```

Understanding Attention and Transformers is one of the most important milestones in becoming an AI Engineer because nearly all modern Generative AI systems are built on Transformer architectures.