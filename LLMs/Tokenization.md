# Tokenization

## What is Tokenization?

Tokenization is the process of converting text into smaller units called **tokens**.

LLMs do not understand words directly.

They understand:

```text
Tokens
```

---

# Example

Text:

```text
I love AI
```

May become:

```text
[1045, 1567, 9932]
```

These numbers are called:

```text
Token IDs
```

---

# Why Tokenization?

Computers process:

```text
Numbers
```

not text.

---

Workflow:

```text
Text
 ↓
Tokens
 ↓
Token IDs
 ↓
Model Input
```

---

# Types of Tokenization

```text
Word Tokenization
Character Tokenization
Subword Tokenization
```

---

# Subword Tokenization

Most modern LLMs use:

```text
Subword Tokenization
```

---

Example

Word:

```text
unbelievable
```

↓

```text
un
believ
able
```

---

Benefits:

```text
Smaller Vocabulary
Handles New Words
Efficient Training
```

---

# Popular Tokenizers

```text
BPE (Byte Pair Encoding)
WordPiece
SentencePiece
tiktoken
```

---

# Example

Word:

```text
ChatGPT
```

Possible Tokens:

```text
Chat
GPT
```

---

# Why Important?

Token count affects:

```text
Cost
Latency
Context Window Usage
```

---

# Embeddings

## What are Embeddings?

Embeddings are dense vector representations of tokens or words.

They convert text into mathematical representations that capture meaning.

---

# Example

Word:

```text
dog
```

Embedding:

```text
[0.42, 0.73, 0.18, ...]
```

---

Word:

```text
cat
```

Embedding:

```text
[0.44, 0.71, 0.20, ...]
```

---

Notice:

```text
Dog and Cat
```

have similar vectors because they have similar meanings.

---

# Why Embeddings?

Traditional Encoding:

```text
Dog = [1,0,0]

Cat = [0,1,0]
```

---

Problem:

```text
No Semantic Meaning
```

---

Embeddings solve this.

---

# Semantic Relationships

Example:

```text
King - Man + Woman
```

≈

```text
Queen
```

---

Embeddings capture:

```text
Meaning
Similarity
Relationships
Context
```

---

# Embedding Workflow

```text
Token
   ↓
Embedding Layer
   ↓
Vector
   ↓
Transformer
```

---

# Types of Embeddings

```text
Word Embeddings
Sentence Embeddings
Document Embeddings
Contextual Embeddings
```

---

# Word Embeddings

Examples:

```text
Word2Vec
GloVe
FastText
```

---

# Contextual Embeddings

Examples:

```text
BERT
GPT
Llama
```

---

Different contexts produce different embeddings.

---

Example

```text
Bank
```

Context 1:

```text
River Bank
```

---

Context 2:

```text
Financial Bank
```

---

Modern embeddings understand the difference.

---

# Embedding Models

Popular models:

- text-embedding-3-small
- text-embedding-3-large
- BGE
- E5

---

# Context Windows

## What is a Context Window?

A Context Window is the amount of information an LLM can remember and process in a single request.

---

Think of it as:

```text
Model Working Memory
```

---

# Example

Input:

```text
Conversation
Documents
Instructions
User Query
```

All must fit inside:

```text
Context Window
```

---

# Visualization

```text
System Prompt
      +
Chat History
      +
Retrieved Documents
      +
User Question
      ↓
Context Window
```

---

# Why Important?

If the context exceeds the limit:

```text
Older Information Is Removed
```

or

```text
Input Is Truncated
```

---

# Example

Context Window:

```text
8,000 Tokens
```

Input:

```text
10,000 Tokens
```

Result:

```text
2,000 Tokens Lost
```

---

# Impact on RAG

RAG Systems use context windows for:

```text
Retrieved Documents
Knowledge Base Chunks
User Questions
```

---

Large Context Windows enable:

```text
More Documents
More Reasoning
Better Responses
```

---

# Context Window Challenges

## Lost in the Middle

Models may pay less attention to information buried in the middle of long contexts.

---

Example:

```text
Important Fact
```

hidden inside:

```text
100 Pages
```

---

May be overlooked.

---

# Context Optimization Techniques

```text
Chunking
Re-Ranking
Compression
Summarization
```

---

# Prompt Engineering

## What is Prompt Engineering?

Prompt Engineering is the practice of designing effective instructions that guide LLM behavior.

---

Goal:

```text
Better Prompt
      ↓
Better Output
```

---

# Basic Prompt

```text
Explain Machine Learning.
```

---

Output:

```text
General Answer
```

---

# Improved Prompt

```text
Explain Machine Learning for a DevOps Engineer transitioning into AI Engineering. Include examples from MLOps and insurance.
```

---

Output:

```text
More Relevant Answer
```

---

# Components of a Good Prompt

```text
Role
Task
Context
Constraints
Output Format
Examples
```

---

# Prompt Structure

```text
Role
  ↓
Task
  ↓
Context
  ↓
Instructions
  ↓
Expected Output
```

---

# Example

```text
You are an AI Infrastructure Engineer.

Explain Kubernetes for LLM deployment.

Use simple language.

Provide examples using vLLM and KServe.
```

---

# Prompting Techniques

## Zero-Shot Prompting

No examples provided.

---

Example:

```text
Translate:

Hello World
```

---

# One-Shot Prompting

One example provided.

---

Example:

```text
English: Hello

French: Bonjour

English: Good Morning
```

---

# Few-Shot Prompting

Multiple examples provided.

---

Benefits:

```text
Higher Accuracy
Better Consistency
```

---

# Chain of Thought Prompting

Encourages step-by-step reasoning.

---

Example:

```text
Solve this problem step by step.
```

---

Benefits:

```text
Better Reasoning
Better Accuracy
```

---

# Role Prompting

Assign a role.

---

Example:

```text
Act as a Senior AI Platform Engineer.
```

---

# Structured Output Prompting

Force a specific format.

---

Example:

```text
Return output in JSON format.
```

---

# Prompt Engineering for RAG

Example:

```text
Answer only using the provided context.

If information is unavailable, say:
"I don't know."
```

---

Benefits:

```text
Reduced Hallucinations
Better Grounding
```

---

# Prompt Engineering for Agents

Example:

```text
Think step by step.

Use tools when necessary.

Verify results before responding.
```

---

# Common Prompting Mistakes

```text
Vague Instructions
Missing Context
Too Much Context
Ambiguous Requirements
No Output Format
```

---

# LLM Workflow

```text
Text
 ↓
Tokenization
 ↓
Embeddings
 ↓
Context Window
 ↓
Transformer Processing
 ↓
Prompt Interpretation
 ↓
Response Generation
```

---

# Insurance Example

User Query:

```text
Predict claim severity.
```

---

Better Prompt:

```text
You are an insurance claims analyst.

Predict claim severity using:

Vehicle Age
Claim Amount
Accident Type

Return:
Severity Level
Risk Score
Explanation
```

---

Result:

```text
More Structured
More Accurate
Business Friendly
```

---

# Interview Questions

### Q1. What is Tokenization?

```text
The process of converting text into tokens that LLMs can process.
```

---

### Q2. What are Embeddings?

```text
Dense vector representations that capture semantic meaning.
```

---

### Q3. What is a Context Window?

```text
The maximum amount of information an LLM can process in a single request.
```

---

### Q4. Why are Embeddings important?

```text
They allow models to understand semantic relationships between words and sentences.
```

---

### Q5. What is Prompt Engineering?

```text
The practice of designing effective prompts to improve LLM outputs.
```

---

# Learning Path

```text
Tokenization
      ↓
Embeddings
      ↓
Vector Similarity
      ↓
Context Windows
      ↓
Prompt Engineering
      ↓
Advanced Prompting
      ↓
RAG
      ↓
Agents
      ↓
LLMOps
```

# Most Important Topics for AI Engineers

```text
Tokenization
BPE
Embeddings
Semantic Search
Vector Similarity
Context Windows
Prompt Engineering
Few-Shot Prompting
Chain of Thought
Role Prompting
Structured Outputs
```

These concepts form the foundation of:

```text
LLMs
RAG Systems
Agentic AI
Chatbots
AI Copilots
Semantic Search
Knowledge Assistants
Generative AI Platforms
```

Before learning Fine-Tuning, RAG, and Agentic AI, every AI Engineer should have a strong understanding of **Tokenization, Embeddings, Context Windows, and Prompt Engineering**.