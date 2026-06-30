# Haystack

## What is Haystack?

Haystack is an open-source AI framework designed for building:

```text
RAG Systems
Semantic Search
Question Answering Systems
Document Intelligence
AI Agents
Enterprise Search
```

Developed by:

:contentReference[oaicite:0]{index=0}

---

# Why Haystack?

LLMs cannot directly access:

```text
PDFs
Databases
Company Documents
Knowledge Bases
```

Haystack helps connect:

```text
Documents
Vector Databases
Retrievers
LLMs
```

into production-ready AI applications.

---

# Core Idea

Haystack is built around:

```text
Pipelines
Components
Retrievers
Generators
```

---

# Real Example

User asks:

```text
What is collision coverage?
```

---

Haystack:

```text
Retrieve Relevant Documents
      ↓
Pass Context To LLM
      ↓
Generate Accurate Answer
```

---

# Haystack Architecture

```text
Documents
      ↓
Document Store
      ↓
Retriever
      ↓
Re-Ranker
      ↓
LLM
      ↓
Answer
```

---

# Main Components

```text
Document Store
Retrievers
Generators
Pipelines
Re-Rankers
Embedders
Agents
```

---

# 1. Document Store

## What is a Document Store?

A place where documents and embeddings are stored.

---

Supported Stores

```text
Elasticsearch
OpenSearch
Qdrant
Pinecone
Weaviate
ChromaDB
PgVector
```

---

Example

```text
Policy Documents
Claims Manuals
Coverage Rules
```

stored in Document Store.

---

# Installation

```bash
pip install haystack-ai
```

---

# Create Documents

```python
from haystack import Document

docs = [

    Document(
        content="Collision coverage pays for vehicle damage."
    ),

    Document(
        content="Comprehensive coverage covers hail damage."
    )
]
```

---

# 2. Embedders

## What are Embedders?

Convert text into vectors.

---

Workflow

```text
Text
 ↓
Embedding Model
 ↓
Vector
```

---

Example

```python
from haystack.components.embedders import (

    SentenceTransformersTextEmbedder
)

embedder = (

    SentenceTransformersTextEmbedder(
        model="all-MiniLM-L6-v2"
    )
)
```

---

# 3. Retriever

## What is a Retriever?

Finds relevant documents.

---

Workflow

```text
Question
 ↓
Retriever
 ↓
Relevant Documents
```

---

Example

```python
Retriever
 ↓
Top K Documents
```

---

Benefits

```text
Fast Search
Semantic Search
```

---

# 4. Generator

## What is a Generator?

An LLM component that generates responses.

---

Examples

- GPT
- Claude
- Gemini
- Llama

---

Example

```python
from haystack.components.generators import (

    OpenAIGenerator
)

generator = OpenAIGenerator()
```

---

Workflow

```text
Context
 ↓
LLM
 ↓
Answer
```

---

# 5. Pipelines

## What is a Pipeline?

A workflow connecting multiple components.

---

Example

```text
Retriever
 ↓
Generator
 ↓
Answer
```

---

Visualization

```text
Question
      ↓
Retriever
      ↓
Generator
      ↓
Answer
```

---

# Basic Pipeline Example

```python
from haystack import Pipeline

pipeline = Pipeline()
```

---

Add Components

```python
pipeline.add_component(
    "retriever",
    retriever
)

pipeline.add_component(
    "generator",
    generator
)
```

---

Connect Components

```python
pipeline.connect(

    "retriever",

    "generator"
)
```

---

# Pipeline Flow

```text
Input
 ↓
Retriever
 ↓
Generator
 ↓
Output
```

---

# Complete RAG Example

```python
from haystack import Pipeline

pipeline = Pipeline()

pipeline.add_component(

    "retriever",

    retriever
)

pipeline.add_component(

    "generator",

    generator
)

pipeline.connect(

    "retriever",

    "generator"
)
```

---

Run Query

```python
result = pipeline.run(

    {
        "retriever":{

            "query":"What is AI?"
        }
    }
)
```

---

# 6. Re-Rankers

## What is Re-Ranking?

Improves retrieval quality.

---

Workflow

```text
Retriever
     ↓
20 Results
     ↓
Re-Ranker
     ↓
Top 5 Results
```

---

Benefits

```text
Higher Accuracy
```

---

Example

```python
from haystack.components.rankers import (

    TransformersSimilarityRanker
)
```

---

# Hybrid Search

Haystack supports:

```text
Dense Search
+
Sparse Search
```

---

Benefits

```text
Better Retrieval
```

---

Workflow

```text
BM25
 +
Embeddings
```

---

# Metadata Filtering

Example

```python
department = claims
```

---

Retrieve Only:

```text
Claims Documents
```

---

Benefits

```text
Targeted Retrieval
```

---

# Haystack + Qdrant

```python
from haystack_integrations.document_stores.qdrant import (

    QdrantDocumentStore
)
```

---

Workflow

```text
Documents
      ↓
Qdrant
      ↓
Retriever
      ↓
Generator
```

---

# Haystack + Pinecone

Workflow

```text
Documents
      ↓
Pinecone
      ↓
Retriever
      ↓
LLM
```

---

# Haystack + OpenSearch

Workflow

```text
Documents
      ↓
OpenSearch
      ↓
Retriever
      ↓
LLM
```

---

# Haystack Agents

Modern Haystack supports:

```text
Tool Calling
Agent Workflows
Reasoning Loops
```

---

Example

```text
Agent
 ↓
Search Tool
 ↓
Database
 ↓
Answer
```

---

# Insurance Claims Assistant Example

Knowledge Base

```text
Policy Documents
Claims Manuals
Coverage Rules
```

---

Question

```text
Does hail damage have coverage?
```

---

Pipeline

```text
Retriever
      ↓
Re-Ranker
      ↓
Generator
      ↓
Answer
```

---

Response

```text
Yes, hail damage is covered under comprehensive coverage.
```

---

# Production Architecture

```text
Documents
      ↓
Embeddings
      ↓
Document Store
      ↓
Retriever
      ↓
Re-Ranker
      ↓
LLM
      ↓
Answer
```

---

# Haystack vs LangChain

| Haystack | LangChain |
|-----------|-----------|
| RAG Focused | General Purpose |
| Search Centric | Workflow Centric |
| Enterprise Search | Agent Ecosystem |
| Strong Retrieval | Strong Tooling |

---

# Haystack vs LlamaIndex

| Haystack | LlamaIndex |
|-----------|-----------|
| Search Oriented | Data Oriented |
| Pipeline Architecture | Index Architecture |
| Strong Enterprise Search | Strong Knowledge Systems |

---

# Haystack vs LangGraph

| Haystack | LangGraph |
|-----------|-----------|
| RAG Framework | Agent Framework |
| Retrieval Focus | Workflow Focus |
| Search Pipelines | State Machines |

---

# Advantages

```text
Strong RAG Support
Enterprise Search
Pipeline Architecture
Hybrid Search
Re-Ranking
Production Ready
```

---

# Limitations

```text
Smaller Community
Less Popular Than LangChain
Less Agent-Focused
```

---

# Real Insurance Use Case

Knowledge Base

```text
Claims Manuals
Coverage Documents
FNOL Records
Policy Rules
```

---

Pipeline

```text
PDF Upload
      ↓
Haystack
      ↓
Retriever
      ↓
Re-Ranker
      ↓
GPT / Claude
      ↓
Claims Assistant
```

---

# Interview Questions

### Q1. What is Haystack?

```text
An open-source framework for building RAG systems, semantic search, and question-answering applications.
```

---

### Q2. What is a Document Store?

```text
A storage layer for documents and embeddings used in retrieval.
```

---

### Q3. What is a Retriever?

```text
A component that finds relevant documents for a query.
```

---

### Q4. Why use Re-Ranking?

```text
To improve retrieval quality by selecting the most relevant results.
```

---

### Q5. Why is Haystack popular in enterprise search?

```text
Because it provides powerful retrieval pipelines, hybrid search, and document intelligence capabilities.
```

---

# Learning Path

```text
Embeddings
      ↓
Document Stores
      ↓
Retrievers
      ↓
Generators
      ↓
Pipelines
      ↓
Re-Rankers
      ↓
Hybrid Search
      ↓
RAG Systems
      ↓
Production Search Platforms
```

# Most Important Topics for AI Engineers

```text
Document Stores
Embedders
Retrievers
Generators
Pipelines
Re-Ranking
Hybrid Search
Metadata Filtering
RAG
Enterprise Search
```

Haystack is an excellent framework for building:

```text
Enterprise Search
Knowledge Assistants
Insurance AI Applications
Document Intelligence Systems
Customer Support Bots
Production RAG Platforms
```

It is particularly strong when the primary goal is **high-quality retrieval, search, and question answering over large document collections**.