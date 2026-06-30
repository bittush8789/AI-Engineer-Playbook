# Qdrant

## What is Qdrant?

Qdrant is an open-source vector database designed for:

```text
Semantic Search
RAG Systems
LLM Applications
AI Agents
Recommendation Systems
Similarity Search
```

Qdrant stores:

```text
Vectors
Documents
Metadata
Payloads
```

and performs:

```text
Vector Search
Hybrid Search
Filtering
Nearest Neighbor Search
```

---

# Why Qdrant?

Traditional Databases:

```text
Exact Match Search
```

---

Qdrant:

```text
Semantic Search
Meaning-Based Search
```

---

Example

Query:

```text
car accident
```

---

Qdrant Retrieves:

```text
vehicle collision

road crash

automobile damage
```

even when exact keywords do not match.

---

# Where is Qdrant Used?

```text
RAG Systems
AI Agents
Enterprise Search
Recommendation Engines
Knowledge Bases
Chatbots
```

---

# Qdrant Architecture

```text
Documents
      ↓
Chunking
      ↓
Embeddings
      ↓
Qdrant Collection
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

in SQL databases.

---

Example

```text
insurance_docs
```

---

Stores:

```text
Vectors
Payloads
IDs
```

---

# Point

Each record in Qdrant is called a:

```text
Point
```

---

A Point Contains:

```text
ID
Vector
Payload
```

---

Example

```json
{
  "id":1,
  "vector":[0.12,0.45,0.89],
  "payload":{
    "department":"claims"
  }
}
```

---

# Payload

Payload means:

```text
Metadata
```

---

Example

```json
{
  "policy":"auto",
  "state":"TX",
  "department":"claims"
}
```

---

Used for:

```text
Filtering
Access Control
Advanced Search
```

---

# Installation

## Docker

```bash
docker run -p 6333:6333 qdrant/qdrant
```

---

## Python Client

```bash
pip install qdrant-client
```

---

## Sentence Transformers

```bash
pip install sentence-transformers
```

---

# Connect to Qdrant

```python
from qdrant_client import QdrantClient

client = QdrantClient(
    host="localhost",
    port=6333
)
```

---

# Create Collection

```python
from qdrant_client.models import VectorParams

client.create_collection(

    collection_name="insurance_docs",

    vectors_config=VectorParams(

        size=384,

        distance="Cosine"
    )
)
```

---

Explanation

```text
size
```

=

```text
Embedding Dimension
```

---

```text
distance
```

=

```text
Similarity Metric
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
from qdrant_client.models import PointStruct

client.upsert(

    collection_name="insurance_docs",

    points=[

        PointStruct(

            id=1,

            vector=embedding.tolist(),

            payload={

                "text":"Collision coverage pays for vehicle damage",

                "department":"claims"
            }
        )
    ]
)
```

---

Stored:

```text
Vector
Payload
ID
```

---

# Search Example

```python
query_embedding = model.encode(
    "car accident"
)

results = client.search(

    collection_name="insurance_docs",

    query_vector=query_embedding.tolist(),

    limit=3
)

print(results)
```

---

Output

```text
Most Similar Documents
```

---

# Complete Example

```python
from qdrant_client import QdrantClient

from qdrant_client.models import (

    PointStruct,
    VectorParams
)

from sentence_transformers import SentenceTransformer

client = QdrantClient(
    host="localhost",
    port=6333
)

client.create_collection(

    collection_name="insurance_docs",

    vectors_config=VectorParams(

        size=384,

        distance="Cosine"
    )
)

model = SentenceTransformer(
    "all-MiniLM-L6-v2"
)

documents = [

    "Collision coverage pays for vehicle damage",

    "Comprehensive coverage covers hail damage",

    "Liability insurance covers third-party losses"
]

for i, doc in enumerate(documents):

    embedding = model.encode(
        doc
    )

    client.upsert(

        collection_name="insurance_docs",

        points=[

            PointStruct(

                id=i,

                vector=embedding.tolist(),

                payload={

                    "text":doc
                }
            )
        ]
    )
```

---

# Metadata Filtering

Store Payload

```python
{
  "department":"claims",
  "policy":"auto"
}
```

---

Search With Filter

```python
from qdrant_client.models import (

    Filter,
    FieldCondition,
    MatchValue
)

results = client.search(

    collection_name="insurance_docs",

    query_vector=query_embedding.tolist(),

    query_filter=Filter(

        must=[

            FieldCondition(

                key="department",

                match=MatchValue(
                    value="claims"
                )
            )
        ]
    )
)
```

---

Benefits

```text
Higher Accuracy
Targeted Search
```

---

# Similarity Metrics

## Cosine Similarity

Most popular for NLP.

```text
Angle Between Vectors
```

---

## Dot Product

Measures:

```text
Vector Alignment
```

---

## Euclidean Distance

Measures:

```text
Straight-Line Distance
```

---

# Hybrid Search

Qdrant supports:

```text
Vector Search
+
Keyword Search
```

---

Benefits:

```text
Better Retrieval Quality
```

---

# HNSW Index

Qdrant uses:

```text
HNSW
```

by default.

---

HNSW:

```text
Hierarchical Navigable Small World
```

---

Benefits:

```text
Fast Search
High Accuracy
Scalable
```

---

# Qdrant in RAG

Workflow

```text
PDF
 ↓
Chunking
 ↓
Embeddings
 ↓
Qdrant
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
Claims Manuals
Coverage Rules
```

---

Question:

```text
Is hail damage covered?
```

---

Qdrant Retrieves:

```text
Comprehensive coverage includes hail damage.
```

---

LLM Response:

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
from langchain_qdrant import Qdrant
```

---

Create Vector Store

```python
vectorstore = Qdrant(
    client=client,
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
from llama_index.vector_stores.qdrant import (
    QdrantVectorStore
)
```

---

Workflow

```text
Documents
      ↓
LlamaIndex
      ↓
Qdrant
      ↓
Retriever
      ↓
LLM
```

---

# Cloud Version

Official Website:

:contentReference[oaicite:0]{index=0}

---

Benefits:

```text
Managed Infrastructure
Auto Scaling
Backups
Monitoring
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
Qdrant
      ↓
Hybrid Search
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

# Qdrant vs FAISS

| Qdrant | FAISS |
|---------|---------|
| Vector Database | Vector Search Library |
| Metadata Support | No Native Metadata |
| API Server | Local Library |
| Production Features | Limited |
| Filtering | Manual |

---

# Qdrant vs ChromaDB

| Qdrant | ChromaDB |
|---------|---------|
| More Scalable | Simpler |
| Better Filtering | Basic Filtering |
| HNSW Native | Simpler Architecture |
| Enterprise Ready | Developer Friendly |

---

# Qdrant vs Pinecone

| Qdrant | Pinecone |
|---------|---------|
| Open Source | Managed Service |
| Self Hosted | Cloud Managed |
| Free Option | Paid |
| Full Control | Easy Operations |

---

# Advantages

```text
Open Source
Fast HNSW Search
Metadata Filtering
Hybrid Search
Production Ready
Easy Deployment
```

---

# Limitations

```text
Operational Management Required
More Complex Than ChromaDB
```

---

# Real Insurance Use Case

Knowledge Base:

```text
Claims Rules
Coverage Documents
FNOL Records
Policy Manuals
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
Qdrant
      ↓
Retriever
      ↓
GPT / Claude / Llama
      ↓
Claims Assistant
```

---

# Interview Questions

### Q1. What is Qdrant?

```text
An open-source vector database optimized for semantic search and RAG applications.
```

---

### Q2. What is a Point in Qdrant?

```text
A record containing an ID, vector, and payload.
```

---

### Q3. What is Payload?

```text
Metadata associated with vectors used for filtering and retrieval.
```

---

### Q4. What indexing algorithm does Qdrant use?

```text
HNSW (Hierarchical Navigable Small World).
```

---

### Q5. Why is Qdrant popular for RAG?

```text
Fast vector search, metadata filtering, hybrid search, and production readiness.
```

---

# Learning Path

```text
Embeddings
      ↓
Vector Databases
      ↓
Qdrant Basics
      ↓
Collections
      ↓
Points
      ↓
Payloads
      ↓
HNSW
      ↓
Hybrid Search
      ↓
RAG Systems
      ↓
Production AI Applications
```

# Most Important Topics for AI Engineers

```text
Qdrant
Collections
Points
Payloads
Metadata Filtering
HNSW
Hybrid Search
Retriever
Semantic Search
RAG Integration
```

Qdrant has become one of the most popular vector databases for modern AI systems because it offers:

```text
Open Source
High Performance
Metadata Filtering
Hybrid Search
Production Scalability
LangChain Integration
LlamaIndex Integration
```

making it an excellent choice for:

```text
Enterprise Search
Knowledge Assistants
Insurance AI Systems
AI Agents
Customer Support Bots
Production RAG Platforms
```