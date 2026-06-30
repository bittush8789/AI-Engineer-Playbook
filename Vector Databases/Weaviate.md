# Weaviate

## What is Weaviate?

Weaviate is an open-source vector database designed for:

```text
Semantic Search
RAG Systems
LLM Applications
AI Agents
Recommendation Systems
Knowledge Graph Search
```

Unlike FAISS, Weaviate is a complete vector database that stores:

```text
Vectors
Documents
Metadata
Relationships
```

and provides:

```text
Vector Search
Hybrid Search
Filtering
GraphQL APIs
```

---

# Why Weaviate?

Traditional Database:

```text
Exact Match Search
```

---

Weaviate:

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

Weaviate Retrieves:

```text
vehicle collision

road crash

automobile damage
```

---

# Where is Weaviate Used?

```text
Enterprise Search
RAG Applications
AI Agents
Knowledge Bases
Document Search
Recommendation Systems
```

---

# Weaviate Architecture

```text
Documents
      ↓
Chunking
      ↓
Embeddings
      ↓
Weaviate
      ↓
Similarity Search
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
InsuranceDocs
```

---

Contains:

```text
Vectors
Documents
Metadata
```

---

# Objects

Each row in Weaviate is called an:

```text
Object
```

---

Example

```json
{
  "title":"Collision Coverage",
  "text":"Collision coverage pays for vehicle damage."
}
```

---

# Vectors

Embedding representation.

Example:

```text
[0.15,0.44,0.89,...]
```

---

# Metadata

Additional information.

Example:

```json
{
  "department":"claims",
  "policy":"auto"
}
```

---

# Installation

## Using Docker

```bash
docker run -d \
  -p 8080:8080 \
  semitechnologies/weaviate
```

---

## Python Client

```bash
pip install weaviate-client
```

---

# Start Weaviate

Local Endpoint:

```text
http://localhost:8080
```

---

# Connect to Weaviate

```python
import weaviate

client = weaviate.Client(
    "http://localhost:8080"
)
```

---

# Create Collection

```python
client.schema.create_class(

    {
        "class":"InsuranceDocs",

        "properties":[

            {
                "name":"text",

                "dataType":["text"]
            }
        ]
    }
)
```

---

Equivalent To:

```text
CREATE TABLE InsuranceDocs
```

---

# Insert Data

```python
client.data_object.create(

    {
        "text":"Collision coverage pays for vehicle damage."
    },

    class_name="InsuranceDocs"
)
```

---

Stored:

```text
Document
Vector
Metadata
```

---

# Search Example

```python
result = client.query.get(

    "InsuranceDocs",

    ["text"]

).with_near_text(

    {
        "concepts":[
            "car accident"
        ]
    }

).do()
```

---

Output

```text
Collision coverage pays for vehicle damage.
```

---

# Automatic Vectorization

One of Weaviate's biggest strengths.

---

Workflow

```text
Text
 ↓
Embedding Model
 ↓
Vector
 ↓
Storage
```

---

Automatically generated.

---

# Example

Insert:

```text
Vehicle Collision
```

---

Weaviate Automatically:

```text
Generates Embedding
Stores Vector
```

---

# Hybrid Search

## What is Hybrid Search?

Combines:

```text
Keyword Search
+
Vector Search
```

---

Example

```python
result = client.query.get(

    "InsuranceDocs",

    ["text"]

).with_hybrid(

    query="collision coverage"
).do()
```

---

Benefits:

```text
Better Accuracy
Best of Both Worlds
```

---

# Metadata Filtering

Store Metadata

```python
{
    "department":"claims",

    "policy":"auto"
}
```

---

Search With Filter

```python
result = client.query.get(

    "InsuranceDocs",

    ["text"]

).with_where(

    {
        "path":["department"],

        "operator":"Equal",

        "valueText":"claims"
    }

).do()
```

---

Benefits:

```text
Targeted Retrieval
```

---

# GraphQL Support

One unique feature of Weaviate.

---

Query Example

```graphql
{
  Get {
    InsuranceDocs {
      text
    }
  }
}
```

---

Benefits:

```text
Flexible Queries
Nested Retrieval
```

---

# Vector Search

Workflow

```text
User Query
      ↓
Embedding
      ↓
Similarity Search
      ↓
Top Matches
```

---

Uses:

```text
Cosine Similarity
```

most commonly.

---

# Generative Search

Modern Weaviate supports:

```text
Retrieval
+
Generation
```

---

Workflow

```text
Question
      ↓
Retrieve Context
      ↓
LLM
      ↓
Answer
```

---

# Example

Query:

```text
What is collision coverage?
```

---

Retrieved:

```text
Collision coverage pays for vehicle damage.
```

---

Generated Response:

```text
Collision coverage covers damage to your vehicle caused by an accident.
```

---

# Weaviate in RAG

Architecture

```text
PDFs
 ↓
Chunking
 ↓
Embeddings
 ↓
Weaviate
 ↓
Retriever
 ↓
LLM
 ↓
Answer
```

---

# Insurance Example

Knowledge Base

```text
Policy Documents
Claims Manuals
Coverage Rules
```

---

Question

```text
Is hail damage covered?
```

---

Weaviate Retrieves

```text
Comprehensive coverage includes hail damage.
```

---

LLM Generates

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
from langchain.vectorstores import Weaviate
```

---

Create Vector Store

```python
vectorstore = Weaviate(
    client
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

# Weaviate + OpenAI

Workflow

```text
OpenAI Embeddings
        ↓
Weaviate
        ↓
Retriever
        ↓
GPT
        ↓
Response
```

---

# Weaviate + LlamaIndex

Workflow

```text
Documents
      ↓
LlamaIndex
      ↓
Weaviate
      ↓
Retriever
      ↓
LLM
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
Weaviate
      ↓
Hybrid Search
      ↓
Retriever
      ↓
Re-Ranker
      ↓
LLM
      ↓
Response
```

---

# Weaviate vs FAISS

| Weaviate | FAISS |
|-----------|-----------|
| Vector Database | Vector Search Library |
| Metadata Support | No Native Metadata |
| Hybrid Search | Manual |
| GraphQL | No |
| Production Features | Limited |

---

# Weaviate vs Pinecone

| Weaviate | Pinecone |
|-----------|-----------|
| Open Source | Managed Service |
| Self Hosted | Cloud Managed |
| GraphQL Support | No |
| More Customizable | Easier Operations |

---

# Weaviate vs ChromaDB

| Weaviate | ChromaDB |
|-----------|-----------|
| Enterprise Features | Lightweight |
| Hybrid Search | Basic Search |
| GraphQL APIs | No |
| Distributed Architecture | Local Friendly |

---

# Advantages

```text
Open Source
Hybrid Search
Metadata Filtering
GraphQL APIs
RAG Friendly
Enterprise Ready
```

---

# Limitations

```text
More Complex Setup
Higher Resource Usage
Learning Curve
```

---

# Real Insurance Use Case

Knowledge Base:

```text
Claims Policies
Coverage Rules
FNOL Documents
Claims Manuals
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
Weaviate
      ↓
Retriever
      ↓
GPT / Claude
      ↓
Claims Assistant
```

---

# Interview Questions

### Q1. What is Weaviate?

```text
An open-source vector database used for semantic search, RAG, and AI applications.
```

---

### Q2. What makes Weaviate unique?

```text
Hybrid Search, GraphQL support, metadata filtering, and automatic vectorization.
```

---

### Q3. What is Hybrid Search?

```text
A combination of keyword search and vector similarity search.
```

---

### Q4. What is an Object in Weaviate?

```text
A stored document containing text, vectors, and metadata.
```

---

### Q5. Why is Weaviate popular for RAG?

```text
Because it provides semantic retrieval, metadata filtering, and enterprise-grade search features.
```

---

# Learning Path

```text
Embeddings
      ↓
Vector Databases
      ↓
Weaviate Basics
      ↓
Collections
      ↓
Objects
      ↓
Hybrid Search
      ↓
Metadata Filtering
      ↓
GraphQL
      ↓
RAG Systems
      ↓
Production AI Platforms
```

# Most Important Topics for AI Engineers

```text
Weaviate
Collections
Objects
Automatic Vectorization
Hybrid Search
Metadata Filtering
GraphQL
Retriever
Semantic Search
RAG Integration
```

Weaviate is one of the strongest choices for enterprise AI applications because it combines:

```text
Vector Search
Keyword Search
Metadata Filtering
GraphQL APIs
RAG Capabilities
Enterprise Scalability
```

making it highly suitable for:

```text
Enterprise Search
Knowledge Assistants
Insurance AI Systems
Customer Support Bots
AI Agents
Production RAG Platforms
```