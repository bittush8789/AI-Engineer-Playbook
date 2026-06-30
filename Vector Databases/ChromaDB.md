# ChromaDB

## What is ChromaDB?

ChromaDB is an open-source Vector Database designed for AI applications, RAG systems, semantic search, and LLM-powered applications.

It stores:

```text
Embeddings (Vectors)
Documents
Metadata
```

and performs:

```text
Similarity Search
Semantic Search
Nearest Neighbor Search
```

---

# Why ChromaDB?

Traditional Databases:

```text
Store Text
Store Numbers
Store Tables
```

---

ChromaDB:

```text
Stores Embeddings
Understands Meaning
Supports Semantic Search
```

---

# Example

Query:

```text
Vehicle Accident
```

---

ChromaDB can retrieve:

```text
Car Crash
Road Collision
Vehicle Damage
```

even if exact keywords don't match.

---

# Where is ChromaDB Used?

```text
RAG Systems
Chatbots
AI Agents
Knowledge Bases
Semantic Search
Document Search
```

---

# ChromaDB Architecture

```text
Documents
      ↓
Chunking
      ↓
Embedding Model
      ↓
Embeddings
      ↓
ChromaDB
      ↓
Similarity Search
      ↓
Retrieved Chunks
```

---

# Core Concepts

## Collection

Similar to:

```text
Table in SQL
```

---

Example

```text
insurance_docs
```

---

Contains:

```text
Documents
Embeddings
Metadata
```

---

# Documents

Actual text.

Example:

```text
Collision coverage pays for vehicle damage.
```

---

# Embeddings

Vector representation.

Example:

```text
[0.12, 0.43, 0.89, ...]
```

---

# Metadata

Extra information.

Example:

```json
{
  "department":"claims",
  "policy":"auto"
}
```

---

# Installation

## Install ChromaDB

```bash
pip install chromadb
```

---

## Install OpenAI

```bash
pip install openai
```

---

## Install Sentence Transformers

```bash
pip install sentence-transformers
```

---

# Creating a ChromaDB Client

```python
import chromadb

client = chromadb.Client()
```

---

# Create Collection

```python
collection = client.create_collection(
    name="insurance_docs"
)
```

---

Think of collection as:

```text
SQL Table
```

---

# Insert Documents

```python
collection.add(

    documents=[
        "Collision coverage pays for vehicle damage",

        "Comprehensive coverage covers hail damage"
    ],

    ids=[
        "doc1",
        "doc2"
    ]
)
```

---

Stored:

```text
Documents
Embeddings
IDs
```

---

# Search Documents

```python
results = collection.query(

    query_texts=[
        "car accident"
    ],

    n_results=2
)

print(results)
```

---

Output

```text
Collision coverage pays for vehicle damage
```

because semantic meaning is similar.

---

# Complete Example

```python
import chromadb

client = chromadb.Client()

collection = client.create_collection(
    name="insurance"
)

collection.add(

    documents=[

        "Collision coverage pays for accident damage",

        "Comprehensive coverage includes hail damage",

        "Liability insurance covers third party losses"
    ],

    ids=[

        "1",

        "2",

        "3"
    ]
)

results = collection.query(

    query_texts=[

        "vehicle accident"
    ],

    n_results=2
)

print(results)
```

---

# Persistent Storage

Default client:

```python
chromadb.Client()
```

stores data in memory.

---

For production:

```python
import chromadb

client = chromadb.PersistentClient(
    path="./chroma_db"
)
```

---

Benefits:

```text
Data Saved On Disk
Persistent Storage
Production Ready
```

---

# Example

```python
client = chromadb.PersistentClient(
    path="./chroma_db"
)

collection = client.get_or_create_collection(
    "claims"
)
```

---

# Using Sentence Transformers

Most production systems use embedding models.

Install:

```bash
pip install sentence-transformers
```

---

Example

```python
from sentence_transformers import SentenceTransformer

model = SentenceTransformer(
    "all-MiniLM-L6-v2"
)

embedding = model.encode(
    "vehicle collision"
)

print(
    embedding.shape
)
```

---

Output

```text
384 Dimensions
```

---

# Custom Embedding Function

```python
from sentence_transformers import SentenceTransformer

model = SentenceTransformer(
    "all-MiniLM-L6-v2"
)

def embed(text):

    return model.encode(text)
```

---

# ChromaDB + Sentence Transformers

```python
import chromadb

from sentence_transformers import SentenceTransformer

model = SentenceTransformer(
    "all-MiniLM-L6-v2"
)

client = chromadb.PersistentClient(
    path="./chroma"
)

collection = client.get_or_create_collection(
    "insurance"
)

documents = [

    "Collision coverage pays for vehicle damage",

    "Comprehensive coverage covers hail damage"
]

embeddings = model.encode(
    documents
).tolist()

collection.add(

    documents=documents,

    embeddings=embeddings,

    ids=["1","2"]
)
```

---

# Similarity Search

Query:

```python
query_embedding = model.encode(
    "car accident"
).tolist()

results = collection.query(

    query_embeddings=[
        query_embedding
    ],

    n_results=2
)

print(results)
```

---

# Metadata Filtering

Store Metadata:

```python
collection.add(

    documents=[
        "Auto Policy"
    ],

    ids=[
        "1"
    ],

    metadatas=[

        {
            "department":"claims"
        }
    ]
)
```

---

Filter Search

```python
results = collection.query(

    query_texts=[
        "policy"
    ],

    where={

        "department":"claims"
    }
)
```

---

# ChromaDB in RAG

## Workflow

```text
PDF
 ↓
Chunking
 ↓
Embeddings
 ↓
ChromaDB
 ↓
Retriever
 ↓
LLM
 ↓
Answer
```

---

# RAG Example

Knowledge Base

```text
Policy Documents
Claims Manuals
Coverage Guidelines
```

---

User Query

```text
Is hail damage covered?
```

---

ChromaDB Retrieves

```text
Comprehensive coverage includes hail damage.
```

---

LLM Generates

```text
Yes, hail damage is covered under comprehensive coverage.
```

---

# ChromaDB + LangChain

Install:

```bash
pip install langchain
pip install langchain-chroma
```

---

Example

```python
from langchain_chroma import Chroma

vectorstore = Chroma(

    persist_directory="./chroma_db",

    embedding_function=embeddings
)
```

---

# ChromaDB + OpenAI Embeddings

```python
from openai import OpenAI

client = OpenAI()
```

---

Use:

```text
OpenAI Embeddings
```

↓

```text
Store In ChromaDB
```

↓

```text
Similarity Search
```

---

# Production Architecture

```text
PDFs
      ↓
Chunking
      ↓
Embeddings
      ↓
ChromaDB
      ↓
Retriever
      ↓
LangChain
      ↓
GPT / Claude / Llama
      ↓
Response
```

---

# Advantages

```text
Open Source
Easy Setup
Lightweight
Fast Similarity Search
Excellent For RAG
Local Deployment
```

---

# Limitations

```text
Not Ideal For Massive Scale
Limited Distributed Features
Less Enterprise Focus
```

---

# ChromaDB vs FAISS

| ChromaDB | FAISS |
|-----------|-----------|
| Database | Vector Index |
| Metadata Support | Limited |
| Easy RAG Setup | Moderate |
| Persistent Storage | Yes |
| Beginner Friendly | Excellent |

---

# ChromaDB vs Pinecone

| ChromaDB | Pinecone |
|-----------|-----------|
| Open Source | Managed Service |
| Free | Paid |
| Local Deployment | Cloud |
| Small-Medium Scale | Enterprise Scale |

---

# Real Insurance Use Case

Knowledge Base:

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
Chunking
      ↓
Embedding Generation
      ↓
ChromaDB
      ↓
Retriever
      ↓
LLM
      ↓
Claims Assistant
```

---

# Interview Questions

### Q1. What is ChromaDB?

```text
An open-source vector database used for storing embeddings and performing semantic search.
```

---

### Q2. Why is ChromaDB used in RAG?

```text
To store document embeddings and retrieve relevant chunks using similarity search.
```

---

### Q3. What is a Collection?

```text
A logical container similar to a table in SQL databases.
```

---

### Q4. What does ChromaDB store?

```text
Documents
Embeddings
Metadata
IDs
```

---

### Q5. Difference between ChromaDB and PostgreSQL?

```text
PostgreSQL stores structured data.

ChromaDB stores vector embeddings for semantic search.
```

---

# Learning Path

```text
Embeddings
      ↓
Vector Databases
      ↓
ChromaDB
      ↓
Similarity Search
      ↓
Metadata Filtering
      ↓
RAG
      ↓
LangChain
      ↓
Production AI Systems
```

# Most Important Topics for AI Engineers

```text
Collections
Documents
Embeddings
Metadata
Similarity Search
Persistent Storage
Sentence Transformers
Retriever
Semantic Search
RAG Integration
```

ChromaDB is often the **best first vector database** for learning RAG because it is:

```text
Simple
Open Source
Easy To Setup
Production Capable
LangChain Compatible
LLM Friendly
```

and is widely used in AI Engineer, LLM Engineer, and Agentic AI projects.