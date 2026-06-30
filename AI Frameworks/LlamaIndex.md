# LlamaIndex

## What is LlamaIndex?

LlamaIndex is an open-source framework designed specifically for:

```text
RAG Systems
Knowledge Assistants
Document Search
Enterprise Search
LLM Data Integration
```

It helps connect:

```text
LLMs
Documents
Databases
APIs
Vector Databases
Knowledge Bases
```

with minimal code.

---

# Why LlamaIndex?

LLMs cannot directly access:

```text
PDFs
Databases
Company Documents
Knowledge Bases
```

---

LlamaIndex bridges this gap.

---

Example

User asks:

```text
What is collision coverage?
```

---

LlamaIndex:

```text
Search Documents
 ↓
Retrieve Context
 ↓
Send To LLM
 ↓
Generate Answer
```

---

# Core Idea

LlamaIndex focuses on:

```text
Data → LLM
```

---

LangChain focuses on:

```text
Workflow → LLM
```

---

# LlamaIndex Architecture

```text
Documents
      ↓
Loaders
      ↓
Chunking
      ↓
Embeddings
      ↓
Index
      ↓
Retriever
      ↓
LLM
      ↓
Answer
```

---

# Main Components

```text
Documents
Loaders
Nodes
Indexes
Retrievers
Query Engines
Vector Stores
Response Synthesizers
```

---

# 1. Documents

Everything starts with documents.

---

Examples

```text
PDF
Word
CSV
Database
Web Pages
Emails
```

---

Insurance Example

```text
Claims Manuals
Policy Documents
Coverage Rules
FNOL Records
```

---

# 2. Loaders

Load data into LlamaIndex.

---

Example

```python
from llama_index.core import (
    SimpleDirectoryReader
)

documents = SimpleDirectoryReader(
    "./data"
).load_data()
```

---

Supported Sources

```text
PDF
DOCX
TXT
CSV
Notion
Google Drive
Confluence
SharePoint
```

---

# 3. Nodes

## What are Nodes?

Documents are split into smaller chunks called:

```text
Nodes
```

---

Example

Document:

```text
100 Pages
```

↓

```text
Node 1

Node 2

Node 3
```

---

Benefits:

```text
Efficient Retrieval
Better Context
```

---

# Node Example

```python
from llama_index.core.node_parser import (

    SentenceSplitter
)

splitter = SentenceSplitter(

    chunk_size=512,

    chunk_overlap=50
)
```

---

# 4. Indexes

## What is an Index?

An index organizes data for retrieval.

---

Popular Index Types

```text
Vector Store Index
Summary Index
Keyword Index
Tree Index
```

---

Most Common:

```text
VectorStoreIndex
```

---

# Create Index

```python
from llama_index.core import (

    VectorStoreIndex
)

index = VectorStoreIndex.from_documents(

    documents
)
```

---

Workflow

```text
Documents
 ↓
Embeddings
 ↓
Index
```

---

# 5. Embeddings

Convert text into vectors.

---

Example

```text
Vehicle Accident
```

↓

```text
[0.14,0.83,0.25,...]
```

---

Purpose:

```text
Semantic Search
```

---

# Embedding Workflow

```text
Node
 ↓
Embedding Model
 ↓
Vector
 ↓
Index
```

---

# 6. Retrievers

## What is a Retriever?

Responsible for finding relevant nodes.

---

Workflow

```text
User Query
 ↓
Retriever
 ↓
Relevant Nodes
```

---

Example

```python
retriever = index.as_retriever()
```

---

Search

```python
nodes = retriever.retrieve(

    "vehicle accident"
)
```

---

# 7. Query Engine

## What is a Query Engine?

Combines:

```text
Retriever
+
LLM
```

---

Example

```python
query_engine = (
    index.as_query_engine()
)
```

---

Query

```python
response = query_engine.query(

    "What is AI?"
)
```

---

# Complete Example

```python
from llama_index.core import (

    SimpleDirectoryReader,

    VectorStoreIndex
)

documents = SimpleDirectoryReader(

    "./data"
).load_data()

index = VectorStoreIndex.from_documents(

    documents
)

query_engine = index.as_query_engine()

response = query_engine.query(

    "What is collision coverage?"
)

print(response)
```

---

# RAG Workflow

```text
PDF
 ↓
Loader
 ↓
Nodes
 ↓
Embeddings
 ↓
Index
 ↓
Retriever
 ↓
LLM
 ↓
Answer
```

---

# LlamaIndex + Vector Databases

Supports:

```text
Pinecone
Qdrant
Weaviate
ChromaDB
Milvus
FAISS
```

---

Example

```python
from llama_index.vector_stores.qdrant import (

    QdrantVectorStore
)
```

---

Workflow

```text
LlamaIndex
      ↓
Qdrant
      ↓
Retriever
      ↓
LLM
```

---

# LlamaIndex + Pinecone

```python
from llama_index.vector_stores.pinecone import (

    PineconeVectorStore
)
```

---

Workflow

```text
Documents
      ↓
Embeddings
      ↓
Pinecone
      ↓
Retriever
      ↓
GPT
```

---

# Response Synthesizer

## Purpose

Combine retrieved chunks into final response.

---

Workflow

```text
Retrieved Nodes
      ↓
Response Synthesizer
      ↓
LLM Answer
```

---

# Query Transformation

LlamaIndex can rewrite queries.

---

Example

Original Query:

```text
What's covered?
```

---

Rewritten Query:

```text
What damages are covered under collision insurance?
```

---

Benefits

```text
Better Retrieval
```

---

# Advanced Retrieval

Supports:

```text
Hybrid Search
Metadata Filtering
Re-Ranking
Recursive Retrieval
```

---

# Metadata Filtering

Example

```python
filters = {

    "department":"claims"
}
```

---

Only retrieve:

```text
Claims Documents
```

---

# Re-Ranking

Workflow

```text
Top 20 Results
      ↓
Re-ranker
      ↓
Top 5 Results
```

---

Benefits

```text
Higher Accuracy
```

---

# LlamaIndex Agents

Supports:

```text
Tool Calling
Function Calling
Agent Workflows
```

---

Example

```text
Agent
 ↓
Retriever
 ↓
Database
 ↓
Answer
```

---

# Insurance Claims Assistant Example

Knowledge Base

```text
Claims Manuals
Coverage Policies
FNOL Rules
```

---

Question

```text
Does comprehensive coverage include hail damage?
```

---

Pipeline

```text
LlamaIndex
      ↓
Retriever
      ↓
Pinecone
      ↓
GPT
      ↓
Response
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
Loaders
      ↓
Chunking
      ↓
Embeddings
      ↓
Vector DB
      ↓
Retriever
      ↓
Query Engine
      ↓
LLM
      ↓
Answer
```

---

# LlamaIndex vs LangChain

| LlamaIndex | LangChain |
|------------|------------|
| Data-Centric | Workflow-Centric |
| Strong RAG Focus | General LLM Apps |
| Better Retrieval Features | Better Tooling |
| Knowledge Systems | Agent Systems |

---

# LlamaIndex vs LangGraph

| LlamaIndex | LangGraph |
|------------|------------|
| Retrieval Framework | Workflow Framework |
| RAG Focused | Agent Focused |
| Knowledge Management | State Management |

---

# Advantages

```text
Excellent RAG Support
Easy Document Ingestion
Advanced Retrieval
Production Ready
Vector DB Integrations
```

---

# Limitations

```text
Less Agent-Oriented
Smaller Ecosystem Than LangChain
```

---

# Real Insurance Use Case

Knowledge Base

```text
Policy Documents
Claims Rules
Coverage Manuals
FNOL Records
```

---

Pipeline

```text
PDF Upload
      ↓
LlamaIndex
      ↓
Chunking
      ↓
Qdrant
      ↓
Retriever
      ↓
GPT
      ↓
Claims Assistant
```

---

# Interview Questions

### Q1. What is LlamaIndex?

```text
A framework for connecting LLMs with external data sources and building RAG applications.
```

---

### Q2. What are Nodes in LlamaIndex?

```text
Chunks of documents used for retrieval and indexing.
```

---

### Q3. What is a Query Engine?

```text
A component that combines retrieval and generation to answer questions.
```

---

### Q4. Why is LlamaIndex popular for RAG?

```text
Because it provides document ingestion, indexing, retrieval, and response synthesis in one framework.
```

---

### Q5. Difference between LlamaIndex and LangChain?

```text
LlamaIndex focuses on data retrieval and RAG.

LangChain focuses on workflows, tools, and agents.
```

---

# Learning Path

```text
Embeddings
      ↓
Vector Databases
      ↓
LlamaIndex Basics
      ↓
Documents
      ↓
Nodes
      ↓
Indexes
      ↓
Retrievers
      ↓
Query Engines
      ↓
Advanced RAG
      ↓
Production AI Systems
```

# Most Important Topics for AI Engineers

```text
Documents
Loaders
Nodes
Indexes
Embeddings
Retrievers
Query Engines
Response Synthesizers
Metadata Filtering
Re-Ranking
Advanced RAG
```

LlamaIndex is one of the most important frameworks for building:

```text
RAG Systems
Enterprise Search
Knowledge Assistants
Insurance AI Applications
Customer Support Bots
Document Intelligence Platforms
```

For AI Engineers working on retrieval systems, **LlamaIndex is often considered the most specialized and powerful framework for RAG and knowledge-centric AI applications.**