# Retrieval-Augmented Generation (RAG)

## What is RAG?

RAG stands for:

```text
Retrieval-Augmented Generation
```

RAG combines:

```text
Information Retrieval
+
Large Language Models (LLMs)
```

to generate accurate and up-to-date responses.

---

# Why RAG?

LLMs have limitations:

```text
Hallucinations
Outdated Knowledge
No Access To Private Data
```

---

Example

Ask an LLM:

```text
What is our company's leave policy?
```

---

Base LLM:

```text
Doesn't Know
```

---

RAG:

```text
Search Company Documents
      ↓
Retrieve Information
      ↓
Generate Accurate Answer
```

---

# Core Idea

Instead of relying only on:

```text
Model Memory
```

RAG uses:

```text
External Knowledge
```

---

# Simple Workflow

```text
User Question
      ↓
Retriever
      ↓
Relevant Documents
      ↓
LLM
      ↓
Answer
```

---

# Example

Question:

```text
What is the deductible for policy ABC?
```

---

Retriever:

```text
Find Policy Document
```

---

LLM:

```text
Read Retrieved Context
```

---

Answer:

```text
Deductible = $500
```

---

# RAG Architecture

## Complete Architecture

```text
                ┌───────────────┐
                │ Knowledge Base │
                └───────┬───────┘
                        │
                        ▼
                 Document Loader
                        │
                        ▼
                  Text Chunking
                        │
                        ▼
                   Embeddings
                        │
                        ▼
                 Vector Database
                        │
────────────────────────────────────
                        │
User Query             ▼
     │          Query Embedding
     │                │
     ▼                ▼
   Retriever ─────► Similarity Search
                        │
                        ▼
              Relevant Chunks Retrieved
                        │
                        ▼
                   Prompt Builder
                        │
                        ▼
                  Large Language Model
                        │
                        ▼
                     Response
```

---

# Main Components

```text
Knowledge Base
Document Loader
Chunking
Embeddings
Vector Database
Retriever
Prompt Builder
LLM
```

---

# 1. Knowledge Base

## What is it?

Collection of documents containing information.

---

Examples:

```text
PDFs
Word Documents
Emails
Policies
Claims Documents
Databases
Web Pages
```

---

Insurance Example:

```text
Policy Documents
Coverage Rules
Claims Guidelines
FNOL Records
```

---

# 2. Document Loader

## Purpose

Loads documents into the RAG pipeline.

---

Input:

```text
PDF
DOCX
TXT
HTML
CSV
```

---

Output:

```text
Raw Text
```

---

Popular Tools:

```text
LangChain Loaders
LlamaIndex Readers
Unstructured.io
```

---

# 3. Chunking

## What is Chunking?

Breaking large documents into smaller pieces.

---

Why?

LLMs cannot process huge documents efficiently.

---

Example

Document:

```text
100 Pages
```

---

Chunked Into:

```text
500 Tokens

500 Tokens

500 Tokens
```

---

Visualization

```text
Large Document
       ↓
Chunk 1
Chunk 2
Chunk 3
Chunk 4
```

---

# Why Chunking Matters?

Poor Chunking:

```text
Information Loss
```

---

Good Chunking:

```text
Better Retrieval
Higher Accuracy
```

---

# 4. Embeddings

## What are Embeddings?

Numerical vector representations of text.

---

Example

Text:

```text
Vehicle Collision
```

↓

```text
[0.12, 0.54, 0.83 ...]
```

---

Purpose:

```text
Capture Semantic Meaning
```

---

# Workflow

```text
Chunk
 ↓
Embedding Model
 ↓
Vector
```

---

Popular Embedding Models

- text-embedding-3-small
- text-embedding-3-large
- BGE
- E5

---

# 5. Vector Database

## What is a Vector Database?

Stores embeddings and performs similarity search.

---

Traditional Database:

```text
Exact Match
```

---

Vector Database:

```text
Semantic Search
```

---

Popular Vector Databases

```text
Pinecone
Weaviate
Qdrant
Milvus
ChromaDB
FAISS
```

---

Example

Query:

```text
Vehicle Accident
```

---

Retrieved:

```text
Car Collision

Road Crash

Vehicle Damage
```

because meanings are similar.

---

# 6. Retriever

## Purpose

Retrieve the most relevant chunks.

---

Workflow

```text
User Query
      ↓
Embedding
      ↓
Similarity Search
      ↓
Top Relevant Chunks
```

---

# Similarity Search

Most commonly:

```text
Cosine Similarity
```

---

Formula:

```text
Similarity

=

cos(θ)
```

---

Higher similarity:

```text
More Relevant
```

---

# 7. Prompt Builder

## Purpose

Combine:

```text
User Question
+
Retrieved Context
```

into a prompt.

---

Example

```text
Context:
Policy deductible is $500.

Question:
What is the deductible?

Answer:
```

---

# 8. Large Language Model

## Purpose

Generate final answer.

---

Input:

```text
Question
+
Retrieved Context
```

---

Output:

```text
Grounded Response
```

---

# End-to-End RAG Flow

```text
User Question
       ↓
Embedding
       ↓
Vector Search
       ↓
Top Chunks
       ↓
Prompt Creation
       ↓
LLM
       ↓
Answer
```

---

# Example

Question:

```text
What does collision coverage include?
```

---

Retrieved Chunk:

```text
Collision coverage pays for vehicle damage caused by accidents.
```

---

LLM Response:

```text
Collision coverage pays for damage to your vehicle resulting from an accident.
```

---

# Why RAG is Better than Fine-Tuning?

| Fine-Tuning | RAG |
|------------|------------|
| Updates Model | Uses External Knowledge |
| Expensive | Cheaper |
| Retraining Needed | No Retraining |
| Static Knowledge | Dynamic Knowledge |

---

# RAG Use Cases

```text
Enterprise Search
Knowledge Assistants
Customer Support
Chatbots
Legal AI
Healthcare AI
Insurance AI
```

---

# Insurance Example

Knowledge Base:

```text
Claims Manuals
Coverage Documents
Policy Rules
FNOL Records
```

---

Question:

```text
Is hail damage covered?
```

---

Retriever:

```text
Find Coverage Rule
```

---

LLM:

```text
Generate Answer
```

---

Response:

```text
Yes, hail damage is covered under comprehensive coverage.
```

---

# Benefits of RAG

```text
Reduces Hallucinations
Uses Latest Information
Works With Private Data
Easy To Update
Cost Effective
```

---

# Challenges

```text
Poor Chunking
Poor Retrieval
Context Window Limits
Embedding Quality
Latency
```

---

# Modern RAG Stack

```text
LangChain
LangGraph
LlamaIndex
OpenAI
Pinecone
Qdrant
ChromaDB
FAISS
```

---

# Interview Questions

### Q1. What is RAG?

```text
A technique that combines retrieval systems with LLMs to generate accurate responses using external knowledge.
```

---

### Q2. Why is RAG needed?

```text
To reduce hallucinations and provide access to external or private data.
```

---

### Q3. What is a Vector Database?

```text
A database optimized for storing embeddings and performing similarity search.
```

---

### Q4. What is the role of embeddings in RAG?

```text
To convert text into vectors for semantic retrieval.
```

---

### Q5. Difference between RAG and Fine-Tuning?

```text
RAG retrieves external information at runtime.

Fine-Tuning updates model weights permanently.
```

---

--------------------------------------------------------

# Chunking Strategies

## What is Chunking?

Chunking is the process of breaking large documents into smaller pieces before generating embeddings and storing them in a vector database.

---

# Why Chunking?

LLMs have:

```text
Context Window Limits
```

Large documents cannot be embedded efficiently.

---

Example

Document:

```text
100 Pages
```

↓

```text
Chunk 1
Chunk 2
Chunk 3
...
```

---

# Good Chunk Characteristics

```text
Semantically Meaningful
Not Too Small
Not Too Large
Contains Complete Context
```

---

# Types of Chunking

## 1. Fixed-Size Chunking

Most common method.

---

Example

```text
Chunk Size = 500 Tokens
```

---

Document:

```text
2000 Tokens
```

↓

```text
Chunk 1 (500)

Chunk 2 (500)

Chunk 3 (500)

Chunk 4 (500)
```

---

Advantages:

```text
Simple
Fast
Easy Implementation
```

---

Disadvantages:

```text
Can Break Context
```

---

# 2. Recursive Chunking

Most popular in production RAG.

---

Hierarchy:

```text
Document
 ↓
Paragraph
 ↓
Sentence
 ↓
Word
```

---

Benefits:

```text
Preserves Context
Better Retrieval
```

---

Used heavily in:

```text
LangChain
LlamaIndex
```

---

# 3. Semantic Chunking

Uses embeddings to determine chunk boundaries.

---

Example

Instead of:

```text
Every 500 Tokens
```

it splits when:

```text
Topic Changes
```

---

Benefits:

```text
Meaningful Chunks
Higher Retrieval Accuracy
```

---

# 4. Sliding Window Chunking

Chunks overlap.

---

Example

```text
Chunk 1

Tokens 1-500
```

---

```text
Chunk 2

Tokens 400-900
```

---

Overlap:

```text
100 Tokens
```

---

Benefits:

```text
Preserves Context
Reduces Information Loss
```

---

# Chunking Best Practices

```text
Chunk Size:
300-1000 Tokens

Overlap:
50-200 Tokens
```

---

# Embeddings

## What are Embeddings?

Embeddings are vector representations of text that capture semantic meaning.

---

Example

Text:

```text
Vehicle Collision
```

↓

```text
[0.23, 0.84, 0.15 ...]
```

---

# Purpose

Convert:

```text
Text
```

into:

```text
Numerical Vectors
```

for similarity search.

---

# Embedding Workflow

```text
Text
 ↓
Embedding Model
 ↓
Vector
 ↓
Vector Database
```

---

# Semantic Similarity

Example

```text
Vehicle Accident
```

and

```text
Car Crash
```

produce similar vectors.

---

# Types of Embeddings

## Word Embeddings

```text
Word2Vec
FastText
GloVe
```

---

## Sentence Embeddings

```text
BGE
E5
Instructor
```

---

## Document Embeddings

```text
Entire Documents
```

represented as vectors.

---

# Embedding Models for RAG

Popular Models:

```text
OpenAI Embeddings
BGE
E5
Instructor
Jina Embeddings
```

---

# Vector Databases

## What is a Vector Database?

A database optimized for storing and searching embeddings.

---

Traditional Database

```text
Exact Match Search
```

---

Vector Database

```text
Semantic Search
```

---

# Workflow

```text
Document
 ↓
Embedding
 ↓
Vector Database
```

---

# Popular Vector Databases

## ChromaDB

Benefits:

```text
Open Source
Lightweight
Easy Development
```

---

## FAISS

Developed by:

:contentReference[oaicite:0]{index=0}

---

Benefits:

```text
Fast Similarity Search
Local Deployment
```

---

## Pinecone

Benefits:

```text
Managed Service
Scalable
Production Ready
```

---

## Qdrant

Benefits:

```text
Fast
Open Source
Metadata Filtering
```

---

## Weaviate

Benefits:

```text
Graph + Vector Search
Hybrid Search
```

---

## Milvus

Benefits:

```text
Large Scale Deployments
Distributed Architecture
```

---

# Retrieval Techniques

## What is Retrieval?

Finding the most relevant information from a knowledge base.

---

Workflow

```text
User Query
 ↓
Retriever
 ↓
Relevant Chunks
```

---

# 1. Dense Retrieval

Uses:

```text
Embeddings
```

---

Benefits:

```text
Semantic Understanding
```

---

Example

Query:

```text
Vehicle Crash
```

---

Retrieves:

```text
Collision
Accident
Vehicle Damage
```

---

# 2. Sparse Retrieval

Uses:

```text
Keywords
```

---

Popular Algorithm:

```text
BM25
```

---

Benefits:

```text
Exact Matching
Fast Search
```

---

# 3. Hybrid Retrieval

Combines:

```text
Dense Retrieval
+
Sparse Retrieval
```

---

Benefits:

```text
Higher Accuracy
```

---

# 4. Metadata Retrieval

Uses:

```text
Tags
Dates
Departments
Categories
```

---

Example

```text
Department = Claims
```

Only retrieve claims documents.

---

# Re-ranking

## What is Re-ranking?

Second-stage filtering of retrieved documents.

---

Workflow

```text
Retriever
     ↓
Top 20 Chunks
     ↓
Re-ranker
     ↓
Top 5 Chunks
```

---

# Why Re-Ranking?

Initial retrieval may return:

```text
Partially Relevant Documents
```

---

Re-ranker improves ordering.

---

# Popular Re-Rankers

```text
Cohere Rerank
BGE Reranker
Cross Encoder Models
```

---

# Example

Query:

```text
Collision Coverage
```

---

Retriever:

```text
20 Results
```

---

Re-ranker:

```text
Most Relevant 5 Results
```

---

# Hybrid Search

## What is Hybrid Search?

Combination of:

```text
Keyword Search
+
Semantic Search
```

---

Formula:

```text
BM25 Score
+
Embedding Similarity Score
```

---

# Why Hybrid Search?

Dense Search:

```text
Great Semantics
```

---

Sparse Search:

```text
Great Exact Matching
```

---

Hybrid:

```text
Best Of Both
```

---

# Example

Query:

```text
Coverage A deductible
```

---

Keyword Search finds:

```text
Coverage A
```

---

Vector Search finds:

```text
Deductible Rules
```

---

Combined:

```text
Higher Quality Results
```

---

# Context Optimization

## What is Context Optimization?

Improving the quality of information sent to the LLM.

---

Goal:

```text
Maximum Information
Minimum Tokens
```

---

# Why Needed?

LLMs have:

```text
Limited Context Windows
```

---

Poor Context:

```text
Irrelevant Information
```

---

Good Context:

```text
Relevant Information
```

---

# Techniques

## 1. Better Chunking

```text
Smaller
Meaningful Chunks
```

---

## 2. Re-ranking

```text
Select Best Documents
```

---

## 3. Context Compression

Remove:

```text
Irrelevant Sentences
```

---

Keep:

```text
Important Facts
```

---

## 4. Summarization

Convert:

```text
Large Context
```

↓

```text
Compact Summary
```

---

## 5. Query Rewriting

Original Query:

```text
What's covered?
```

---

Rewrite:

```text
What vehicle damages are covered under collision insurance?
```

---

Improves retrieval.

---

## 6. Context Window Management

Prioritize:

```text
Most Relevant Chunks
```

---

Avoid:

```text
Context Overflow
```

---

# Advanced RAG Architecture

```text
Knowledge Base
      ↓
Chunking
      ↓
Embeddings
      ↓
Vector Database
      ↓
Hybrid Search
      ↓
Retriever
      ↓
Re-ranker
      ↓
Context Optimization
      ↓
Prompt Builder
      ↓
LLM
      ↓
Response
```

---

# Insurance Example

Knowledge Base:

```text
Policy Documents
Claims Manuals
Coverage Rules
```

---

Query:

```text
Is hail damage covered?
```

---

Pipeline:

```text
Hybrid Search
      ↓
Retrieve Chunks
      ↓
Re-rank Results
      ↓
Optimize Context
      ↓
LLM Answer
```

---

Response:

```text
Hail damage is covered under comprehensive coverage.
```

---

# Interview Questions

### Q1. Why is Chunking important in RAG?

```text
It improves retrieval quality and helps fit documents into LLM context windows.
```

---

### Q2. What is a Vector Database?

```text
A database designed to store embeddings and perform similarity search.
```

---

### Q3. What is Re-ranking?

```text
A second-stage retrieval process that improves document relevance ordering.
```

---

### Q4. What is Hybrid Search?

```text
A combination of keyword-based and semantic search.
```

---

### Q5. What is Context Optimization?

```text
The process of maximizing relevant information while minimizing token usage.
```

---

# Learning Path

```text
Embeddings
      ↓
Chunking
      ↓
Vector Databases
      ↓
Dense Retrieval
      ↓
Sparse Retrieval
      ↓
Hybrid Search
      ↓
Re-ranking
      ↓
Context Optimization
      ↓
Production RAG
      ↓
Agentic RAG
```

# Most Important Topics for AI Engineers

```text
Chunking Strategies
Recursive Chunking
Semantic Chunking
Embeddings
Vector Databases
Dense Retrieval
Sparse Retrieval
Hybrid Search
Re-ranking
Context Compression
Query Rewriting
Context Optimization
```

These concepts are the foundation of building production-grade:

```text
Enterprise Search
Knowledge Assistants
Insurance AI Systems
Customer Support Bots
Agentic RAG
AI Copilots
LLM Applications
```

Mastering these topics is essential for becoming an **AI Engineer, LLM Engineer, RAG Engineer, AI Platform Engineer, or Agentic AI Developer**.