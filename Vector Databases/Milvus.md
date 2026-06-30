# Milvus

## What is Milvus?

Milvus is an open-source, distributed vector database designed for:

```text
Semantic Search
RAG Systems
LLM Applications
Recommendation Systems
AI Agents
Large-Scale Similarity Search
```

Milvus is built to handle:

```text
Millions
Billions
Trillions
```

of vectors efficiently.

---

# Why Milvus?

Traditional Databases:

```text
Exact Match Search
```

---

Milvus:

```text
Vector Search
Semantic Search
Nearest Neighbor Search
```

---

Example

Query:

```text
vehicle accident
```

---

Milvus Retrieves:

```text
car collision

road crash

vehicle damage
```

based on meaning instead of exact keywords.

---

# Where is Milvus Used?

```text
Enterprise RAG
AI Search Engines
Recommendation Systems
Chatbots
Computer Vision
GenAI Platforms
```

---

# Milvus Architecture

```text
Documents
      ↓
Chunking
      ↓
Embeddings
      ↓
Milvus Collection
      ↓
Vector Search
      ↓
Retrieved Chunks
      ↓
LLM
      ↓
Response
```

---

# Core Concepts

## Collection

Equivalent to:

```text
Table
```

in SQL.

---

Example

```text
insurance_docs
```

---

Contains:

```text
Vectors
Metadata
IDs
```

---

# Entity

Each stored record is called an:

```text
Entity
```

---

Example

```json
{
  "id":1,
  "vector":[0.15,0.44,0.91],
  "text":"Collision coverage pays for vehicle damage"
}
```

---

# Vector

Embedding representation.

Example

```text
Vehicle Accident
```

↓

```text
[0.22,0.65,0.11,...]
```

---

# Metadata

Additional information.

Example

```json
{
  "department":"claims",
  "policy":"auto"
}
```

---

Used for:

```text
Filtering
Security
Targeted Retrieval
```

---

# Installation

## Docker

```bash
docker compose up -d
```

Official deployment usually runs:

```text
Milvus
Etcd
MinIO
```

---

## Python SDK

```bash
pip install pymilvus
```

---

## Embedding Model

```bash
pip install sentence-transformers
```

---

# Connect to Milvus

```python
from pymilvus import connections

connections.connect(

    alias="default",

    host="localhost",

    port="19530"
)
```

---

# Create Collection

```python
from pymilvus import (

    Collection,
    CollectionSchema,
    FieldSchema,
    DataType
)

id_field = FieldSchema(

    name="id",

    dtype=DataType.INT64,

    is_primary=True
)

vector_field = FieldSchema(

    name="embedding",

    dtype=DataType.FLOAT_VECTOR,

    dim=384
)

schema = CollectionSchema(

    fields=[

        id_field,

        vector_field
    ]
)

collection = Collection(

    name="insurance_docs",

    schema=schema
)
```

---

# Generate Embeddings

```python
from sentence_transformers import SentenceTransformer

model = SentenceTransformer(
    "all-MiniLM-L6-v2"
)

embedding = model.encode(
    "Collision coverage"
)
```

---

# Insert Data

```python
data = [

    [1],

    [embedding.tolist()]
]

collection.insert(data)
```

---

Stored:

```text
ID
Vector
```

---

# Search Example

```python
results = collection.search(

    data=[query_embedding],

    anns_field="embedding",

    limit=3
)
```

---

Output

```text
Most Similar Documents
```

---

# Complete Example

```python
from sentence_transformers import SentenceTransformer

from pymilvus import *

connections.connect(

    host="localhost",

    port="19530"
)

model = SentenceTransformer(
    "all-MiniLM-L6-v2"
)

documents = [

    "Collision coverage pays for vehicle damage",

    "Comprehensive coverage covers hail damage",

    "Liability insurance covers third-party losses"
]

embeddings = model.encode(
    documents
)

data = [

    [1,2,3],

    embeddings.tolist()
]

collection.insert(
    data
)

query_embedding = model.encode(
    "car accident"
)

results = collection.search(

    data=[query_embedding],

    anns_field="embedding",

    limit=2
)

print(results)
```

---

# Indexing in Milvus

Milvus supports multiple indexing algorithms.

---

# FLAT Index

```text
Brute Force Search
```

---

Advantages:

```text
100% Accurate
```

---

Disadvantages:

```text
Slow For Large Data
```

---

# IVF_FLAT

```text
Inverted File Index
```

---

Workflow

```text
Cluster Data
      ↓
Search Cluster
      ↓
Retrieve Results
```

---

Benefits:

```text
Fast Search
```

---

# HNSW

```text
Hierarchical Navigable Small World
```

---

Benefits:

```text
High Accuracy
Very Fast
```

---

# Example

```python
collection.create_index(

    field_name="embedding",

    index_params={

        "index_type":"HNSW",

        "metric_type":"COSINE",

        "params":{"M":16}
    }
)
```

---

# Similarity Metrics

## Cosine Similarity

Most common for NLP.

---

Measures:

```text
Angle Between Vectors
```

---

# Euclidean Distance

Measures:

```text
Straight-Line Distance
```

---

# Dot Product

Measures:

```text
Vector Alignment
```

---

# Metadata Filtering

Milvus supports:

```text
Scalar Filtering
```

---

Example

```python
expr = 'department == "claims"'
```

---

Search:

```python
results = collection.search(

    data=[query_embedding],

    expr=expr,

    limit=5
)
```

---

Benefits:

```text
Targeted Search
Better Results
```

---

# Milvus in RAG

Workflow

```text
PDF
 ↓
Chunking
 ↓
Embeddings
 ↓
Milvus
 ↓
Retriever
 ↓
LLM
 ↓
Answer
```

---

# Insurance Example

Knowledge Base:

```text
Policy Documents
Coverage Rules
Claims Manuals
```

---

Question:

```text
Does comprehensive coverage cover hail damage?
```

---

Milvus Retrieves:

```text
Comprehensive coverage covers hail damage.
```

---

LLM Generates:

```text
Yes, hail damage is covered under comprehensive coverage.
```

---

# LangChain Integration

Install

```bash
pip install langchain
```

---

Example

```python
from langchain.vectorstores import Milvus
```

---

Create Vector Store

```python
vectorstore = Milvus(
    collection_name="insurance_docs"
)
```

---

Search

```python
docs = vectorstore.similarity_search(
    "vehicle accident"
)
```

---

# LlamaIndex Integration

```python
from llama_index.vector_stores.milvus import (
    MilvusVectorStore
)
```

---

Workflow

```text
Documents
      ↓
LlamaIndex
      ↓
Milvus
      ↓
Retriever
      ↓
LLM
```

---

# Milvus Cloud

Official Platform:

:contentReference[oaicite:0]{index=0}

---

Benefits:

```text
Managed Milvus
Auto Scaling
Monitoring
Backups
```

---

# Production Architecture

```text
Documents
      ↓
Chunking
      ↓
Embeddings
      ↓
Milvus
      ↓
Retriever
      ↓
Re-ranker
      ↓
LLM
      ↓
Response
```

---

# Milvus vs FAISS

| Milvus | FAISS |
|---------|---------|
| Vector Database | Search Library |
| Distributed | Local |
| Metadata Support | External |
| Enterprise Ready | Developer Tool |

---

# Milvus vs Pinecone

| Milvus | Pinecone |
|---------|---------|
| Open Source | Managed Service |
| Self Hosted | Cloud Managed |
| More Control | Easier Operations |
| Free Option | Paid |

---

# Milvus vs Qdrant

| Milvus | Qdrant |
|---------|---------|
| Better For Billions of Vectors | Easier Setup |
| Distributed Architecture | Simpler Operations |
| Enterprise Scale | Mid-Large Scale |

---

# Advantages

```text
Open Source
Distributed Architecture
Massive Scale Support
Enterprise Ready
Multiple Index Types
High Performance
```

---

# Limitations

```text
Complex Setup
Higher Resource Requirements
Operational Overhead
```

---

# Real Insurance Use Case

Knowledge Base:

```text
Claims Rules
Policy Documents
FNOL Records
Coverage Manuals
```

---

Pipeline

```text
PDF Upload
      ↓
Chunking
      ↓
Embeddings
      ↓
Milvus
      ↓
Retriever
      ↓
GPT / Claude / Llama
      ↓
Claims Assistant
```

---

# Interview Questions

### Q1. What is Milvus?

```text
An open-source distributed vector database designed for large-scale similarity search.
```

---

### Q2. What is a Collection in Milvus?

```text
A container used to store vectors and related data, similar to a table in SQL.
```

---

### Q3. What indexing algorithms does Milvus support?

```text
FLAT
IVF
HNSW
DiskANN
```

---

### Q4. Why is Milvus used in RAG?

```text
To store embeddings and perform scalable semantic retrieval.
```

---

### Q5. When should you choose Milvus?

```text
When building large-scale AI systems with millions or billions of vectors.
```

---

# Learning Path

```text
Embeddings
      ↓
Vector Databases
      ↓
Milvus Basics
      ↓
Collections
      ↓
Indexing
      ↓
HNSW
      ↓
Metadata Filtering
      ↓
RAG Systems
      ↓
Distributed Search
      ↓
Enterprise AI Platforms
```

# Most Important Topics for AI Engineers

```text
Milvus
Collections
Entities
Embeddings
HNSW
IVF
Cosine Similarity
Metadata Filtering
Retriever
RAG Integration
Distributed Architecture
```

Milvus is one of the strongest choices for enterprise-scale AI systems because it provides:

```text
Massive Scalability
Distributed Search
Production Readiness
Open Source Flexibility
RAG Support
LLM Integration
```

making it highly suitable for:

```text
Enterprise Search
Insurance AI Platforms
Knowledge Assistants
AI Agents
Recommendation Systems
Large-Scale RAG Applications
```