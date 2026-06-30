# LangChain

## What is LangChain?

LangChain is an open-source framework used to build:

```text
LLM Applications
RAG Systems
AI Agents
Chatbots
Multi-Agent Systems
LLM Workflows
```

It provides building blocks to connect:

```text
LLMs
Tools
Databases
Vector Stores
APIs
Memory
Agents
```

into production AI applications.

---

# Why LangChain?

Without LangChain:

```text
User
 ↓
LLM
 ↓
Response
```

---

With LangChain:

```text
User
 ↓
LLM
 ↓
Tools
 ↓
Databases
 ↓
Vector Search
 ↓
Memory
 ↓
Response
```

---

# Real Example

User asks:

```text
What is collision coverage?
```

---

LangChain:

```text
Search Vector DB
 ↓
Retrieve Documents
 ↓
Send Context To LLM
 ↓
Generate Accurate Response
```

---

# LangChain Architecture

```text
User Query
      ↓
Prompt
      ↓
LLM
      ↓
Chains
      ↓
Tools
      ↓
Memory
      ↓
Output
```

---

# Core Components

```text
Models
Prompts
Chains
Memory
Tools
Agents
Retrievers
Vector Stores
```

---

# 1. Models

LangChain connects to LLMs.

Examples:

- GPT
- Claude
- Gemini
- Llama

---

## Installation

```bash
pip install langchain
pip install langchain-openai
```

---

## Example

```python
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(
    model="gpt-4o"
)

response = llm.invoke(
    "What is AI?"
)

print(response.content)
```

---

# 2. Prompts

Prompts define how the model behaves.

---

Example

```python
from langchain.prompts import PromptTemplate

prompt = PromptTemplate(

    input_variables=["topic"],

    template="""
    Explain {topic}
    in simple terms.
    """
)
```

---

Usage

```python
prompt.format(
    topic="Machine Learning"
)
```

---

Output

```text
Explain Machine Learning in simple terms.
```

---

# 3. Chains

## What is a Chain?

A sequence of operations.

---

Example

```text
Prompt
   ↓
LLM
   ↓
Output
```

---

Python Example

```python
from langchain.chains import LLMChain

chain = LLMChain(

    llm=llm,

    prompt=prompt
)

response = chain.run(
    "Deep Learning"
)
```

---

# Chain Workflow

```text
Input
  ↓
Prompt
  ↓
LLM
  ↓
Response
```

---

# 4. Memory

## What is Memory?

Allows the chatbot to remember previous conversations.

---

Without Memory

```text
User:
My name is Bittu.

User:
What's my name?

AI:
I don't know.
```

---

With Memory

```text
AI:
Your name is Bittu.
```

---

Example

```python
from langchain.memory import (
    ConversationBufferMemory
)

memory = ConversationBufferMemory()
```

---

# Memory Types

```text
ConversationBufferMemory
ConversationSummaryMemory
ConversationWindowMemory
```

---

# 5. Tools

## What are Tools?

Functions that agents can use.

---

Examples

```text
Calculator
Search Engine
Database Query
Weather API
Python Execution
```

---

Example Tool

```python
from langchain.tools import tool

@tool
def multiply(a:int,b:int):

    return a*b
```

---

Usage

```text
Agent
 ↓
Tool
 ↓
Result
```

---

# 6. Agents

## What is an Agent?

An AI system that decides:

```text
What To Do
Which Tool To Use
When To Use It
```

---

Traditional Workflow

```text
Input
 ↓
LLM
 ↓
Output
```

---

Agent Workflow

```text
Input
 ↓
Reason
 ↓
Select Tool
 ↓
Execute Tool
 ↓
Generate Answer
```

---

Example

User:

```text
What is 25 × 30?
```

---

Agent:

```text
Uses Calculator Tool
```

---

Returns:

```text
750
```

---

# Agent Architecture

```text
User Query
      ↓
Agent
      ↓
Reasoning
      ↓
Tool Selection
      ↓
Execution
      ↓
Response
```

---

# 7. Vector Stores

LangChain supports:

```text
ChromaDB
FAISS
Pinecone
Weaviate
Qdrant
Milvus
```

---

Example

```python
from langchain.vectorstores import FAISS
```

---

Create Vector Store

```python
vectorstore = FAISS.from_texts(
    texts,
    embeddings
)
```

---

# 8. Retrievers

## What is a Retriever?

Responsible for finding relevant documents.

---

Workflow

```text
Question
 ↓
Retriever
 ↓
Relevant Chunks
```

---

Example

```python
retriever = vectorstore.as_retriever()
```

---

Search

```python
docs = retriever.invoke(
    "car accident"
)
```

---

# LangChain + RAG

## Complete RAG Flow

```text
PDF
 ↓
Chunking
 ↓
Embeddings
 ↓
Vector Database
 ↓
Retriever
 ↓
Prompt
 ↓
LLM
 ↓
Answer
```

---

# Example

Knowledge Base:

```text
Claims Manuals
Coverage Rules
Policies
```

---

Question:

```text
Is hail damage covered?
```

---

Retriever:

```text
Find Relevant Documents
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

# Text Splitters

Used for:

```text
Chunking
```

---

Example

```python
from langchain.text_splitter import (

    RecursiveCharacterTextSplitter
)
```

---

Create Splitter

```python
splitter = RecursiveCharacterTextSplitter(

    chunk_size=500,

    chunk_overlap=100
)
```

---

# Document Loaders

Load:

```text
PDF
DOCX
CSV
TXT
HTML
```

---

Example

```python
from langchain.document_loaders import (

    PyPDFLoader
)
```

---

Load PDF

```python
loader = PyPDFLoader(
    "policy.pdf"
)

docs = loader.load()
```

---

# Output Parsers

Convert model output into structured data.

---

Example

```python
JSON
XML
Pydantic Models
```

---

# LangChain Expression Language (LCEL)

Modern LangChain uses:

```text
LCEL
```

---

Example

```python
chain = prompt | llm
```

---

Benefits

```text
Cleaner Code
Composable Pipelines
Faster Development
```

---

# Production Architecture

```text
User Query
      ↓
Prompt
      ↓
Retriever
      ↓
Vector DB
      ↓
LLM
      ↓
Parser
      ↓
Response
```

---

# Insurance Claims Assistant Example

Knowledge Base

```text
Coverage Documents
Claims Manuals
FNOL Guidelines
```

---

User Query

```text
What is collision coverage?
```

---

Pipeline

```text
LangChain
      ↓
Retriever
      ↓
Pinecone
      ↓
GPT
      ↓
Answer
```

---

Response

```text
Collision coverage pays for damage to your vehicle caused by an accident.
```

---

# Advantages

```text
Fast Development
Large Ecosystem
RAG Support
Agent Support
Tool Integration
Vector DB Integration
```

---

# Limitations

```text
Learning Curve
Frequent API Changes
Can Become Complex
```

---

# Interview Questions

### Q1. What is LangChain?

```text
An open-source framework for building LLM-powered applications.
```

---

### Q2. What are Chains?

```text
Sequences of operations connecting prompts, models, and outputs.
```

---

### Q3. What is a Retriever?

```text
A component that retrieves relevant documents from a vector store.
```

---

### Q4. What is an Agent?

```text
An AI system that decides which tools to use and how to solve tasks.
```

---

### Q5. Why is LangChain popular?

```text
Because it simplifies building RAG systems, agents, and production LLM applications.
```

---

# Learning Path

```text
LLMs
      ↓
Prompts
      ↓
Chains
      ↓
Memory
      ↓
Tools
      ↓
Agents
      ↓
Retrievers
      ↓
Vector Databases
      ↓
RAG
      ↓
Production AI Systems
```

# Most Important Topics for AI Engineers

```text
Prompt Templates
Chains
LCEL
Memory
Tools
Agents
Retrievers
Vector Stores
Document Loaders
Text Splitters
RAG
```

LangChain is one of the most important frameworks in AI Engineering because it provides a complete toolkit for building:

```text
RAG Systems
AI Agents
Chatbots
Knowledge Assistants
Enterprise AI Applications
Insurance AI Solutions
Production LLM Platforms
```

It is often the first framework AI Engineers learn before moving to more advanced orchestration frameworks such as **LangGraph** and multi-agent systems.