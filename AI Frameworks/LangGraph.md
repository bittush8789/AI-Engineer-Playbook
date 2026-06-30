# LangGraph

## What is LangGraph?

LangGraph is a framework built on top of LangChain for creating:

```text
Stateful AI Agents
Multi-Agent Systems
Agent Workflows
Long-Running Workflows
Complex AI Applications
```

Developed by:

:contentReference[oaicite:0]{index=0}

---

# Why LangGraph?

Traditional LangChain chains work well for:

```text
Simple Workflows
Linear Pipelines
```

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

But real AI applications require:

```text
Decision Making
Loops
Agent Collaboration
Memory
Human Approval
```

---

This is where LangGraph comes in.

---

# LangChain vs LangGraph

## LangChain

```text
Linear Workflow
```

Example:

```text
Prompt
 ↓
LLM
 ↓
Answer
```

---

## LangGraph

```text
Graph-Based Workflow
```

Example:

```text
Agent
 ↓
Tool
 ↓
Decision
 ↓
Another Agent
 ↓
Answer
```

---

# Core Idea

LangGraph models workflows as:

```text
Nodes
Edges
State
```

---

Think of it as:

```text
Workflow Engine
For AI Agents
```

---

# LangGraph Architecture

```text
User Query
      ↓
State
      ↓
Node
      ↓
Decision
      ↓
Next Node
      ↓
Response
```

---

# Key Components

```text
State
Nodes
Edges
Graph
Conditional Routing
Memory
Agents
```

---

# 1. State

## What is State?

State stores information throughout workflow execution.

---

Example

```python
{
   "question":"What is AI?",

   "documents":[],

   "answer":""
}
```

---

Why Needed?

Because multiple agents need shared memory.

---

# State Flow

```text
Input
 ↓
State Updated
 ↓
Agent Uses State
 ↓
State Updated Again
```

---

# 2. Nodes

## What is a Node?

A node is a step in the workflow.

---

Examples

```text
LLM Node
Retriever Node
Tool Node
Human Approval Node
```

---

Example

```python
def retrieve_node(state):

    documents = retriever.invoke(
        state["question"]
    )

    state["documents"] = documents

    return state
```

---

# Visualization

```text
Node A
 ↓
Node B
 ↓
Node C
```

---

# 3. Edges

## What is an Edge?

Defines how nodes connect.

---

Example

```text
Retrieve
      ↓
Generate
      ↓
Answer
```

---

Edges define:

```text
Execution Flow
```

---

# Graph Representation

```text
START
  ↓
Retrieve
  ↓
Generate
  ↓
END
```

---

# 4. Conditional Routing

## What is Conditional Routing?

Allows dynamic decisions.

---

Example

```text
Question
      ↓
Need Retrieval?
      ↓
YES → Retriever

NO  → LLM
```

---

This enables:

```text
Agent Decision Making
```

---

# Example

```python
def router(state):

    if state["needs_search"]:

        return "retriever"

    return "llm"
```

---

# 5. Memory

LangGraph supports:

```text
Persistent Memory
Conversation Memory
Checkpointing
```

---

Benefits:

```text
Long-Term Context
Workflow Recovery
```

---

# Example

User:

```text
My name is Bittu.
```

---

Later:

```text
What's my name?
```

---

Agent:

```text
Your name is Bittu.
```

---

# Installation

```bash
pip install langgraph
```

---

# Basic Example

```python
from typing import TypedDict

class State(TypedDict):

    question: str

    answer: str
```

---

Create Node

```python
def llm_node(state):

    state["answer"] = (

        "Artificial Intelligence"
    )

    return state
```

---

# Create Graph

```python
from langgraph.graph import (
    StateGraph
)

graph = StateGraph(State)

graph.add_node(
    "llm",
    llm_node
)
```

---

Add Edge

```python
graph.set_entry_point(
    "llm"
)
```

---

Compile

```python
app = graph.compile()
```

---

Run

```python
app.invoke(

    {
        "question":"What is AI?"
    }
)
```

---

# Complete Workflow

```text
Question
    ↓
Retrieve Documents
    ↓
Generate Answer
    ↓
Review Answer
    ↓
Return Response
```

---

# LangGraph + RAG

## Architecture

```text
User Query
      ↓
Retriever
      ↓
Vector Database
      ↓
LLM
      ↓
Response
```

---

Implementation

```text
Node 1 → Retrieve

Node 2 → Generate

Node 3 → Validate

Node 4 → Respond
```

---

# Multi-Agent Systems

## What is Multi-Agent AI?

Multiple AI agents collaborate.

---

Example

```text
Research Agent
      ↓
Writer Agent
      ↓
Reviewer Agent
```

---

LangGraph excels at this.

---

# Multi-Agent Architecture

```text
User Query
      ↓
Research Agent
      ↓
Planning Agent
      ↓
Writer Agent
      ↓
Reviewer Agent
      ↓
Final Answer
```

---

# Insurance Claims Example

Workflow

```text
FNOL
 ↓
Coverage Agent
 ↓
Fraud Agent
 ↓
Severity Agent
 ↓
Routing Agent
 ↓
Claims Handler
```

---

Implemented naturally using LangGraph.

---

# Tool Calling

LangGraph agents can call:

```text
Search APIs
Databases
Python Functions
External Tools
```

---

Example

```text
Question
 ↓
Agent
 ↓
Search Tool
 ↓
Result
 ↓
Answer
```

---

# Human-in-the-Loop

## What is HITL?

Human approval before continuing.

---

Workflow

```text
Agent
 ↓
Decision
 ↓
Human Review
 ↓
Continue
```

---

Useful for:

```text
Insurance Claims
Legal Systems
Healthcare
```

---

# Checkpointing

Allows workflow recovery.

---

Example

```text
Step 1 Complete
Step 2 Complete
Crash
```

---

Resume:

```text
Step 3
```

---

instead of restarting.

---

# Agent State Example

```python
{
   "question":"What is collision coverage?",

   "documents":[...],

   "answer":"...",

   "needs_review":False
}
```

---

# Production AI Architecture

```text
User Query
      ↓
LangGraph
      ↓
Retriever
      ↓
Pinecone/Qdrant
      ↓
LLM
      ↓
Tool Calls
      ↓
Validation
      ↓
Response
```

---

# LangGraph + LangChain

Relationship

```text
LangChain
     ↓
Building Blocks
```

---

```text
LangGraph
     ↓
Workflow Orchestration
```

---

Together:

```text
Complete AI Platform
```

---

# LangGraph vs LangChain

| LangChain | LangGraph |
|------------|------------|
| Linear Pipelines | Graph Workflows |
| Simple Apps | Complex Agents |
| Chains | State Machines |
| Basic RAG | Multi-Agent RAG |
| Prompt → Output | Stateful Workflows |

---

# LangGraph vs CrewAI

| LangGraph | CrewAI |
|------------|------------|
| Workflow Oriented | Role Oriented |
| Highly Flexible | Easier Setup |
| Production Focus | Agent Collaboration |
| Explicit State | Implicit State |

---

# Advantages

```text
State Management
Multi-Agent Support
Conditional Routing
Checkpointing
Human Approval
Production Ready
```

---

# Limitations

```text
Learning Curve
More Complex Than LangChain
Requires Workflow Design
```

---

# Real Insurance Use Case

Claims Automation System

```text
FNOL Agent
      ↓
Coverage Verification Agent
      ↓
Fraud Detection Agent
      ↓
Severity Prediction Agent
      ↓
Decision Agent
      ↓
Adjuster Routing Agent
```

---

Each step:

```text
Separate Node
```

---

Managed by:

```text
LangGraph Workflow
```

---

# Interview Questions

### Q1. What is LangGraph?

```text
A framework for building stateful, multi-agent AI applications using graph-based workflows.
```

---

### Q2. Why use LangGraph instead of LangChain?

```text
LangGraph supports state management, conditional routing, loops, and multi-agent orchestration.
```

---

### Q3. What is State in LangGraph?

```text
Shared data that moves through workflow nodes.
```

---

### Q4. What is a Node?

```text
A processing step in the workflow.
```

---

### Q5. What is Conditional Routing?

```text
The ability to dynamically choose the next workflow step based on state.
```

---

# Learning Path

```text
LLMs
      ↓
LangChain
      ↓
RAG
      ↓
Agents
      ↓
LangGraph
      ↓
State Management
      ↓
Conditional Routing
      ↓
Multi-Agent Systems
      ↓
Agentic AI
      ↓
Production AI Platforms
```

# Most Important Topics for AI Engineers

```text
State
Nodes
Edges
Graphs
Conditional Routing
Memory
Checkpointing
Tool Calling
Multi-Agent Systems
Human-in-the-Loop
```

LangGraph is currently one of the most important frameworks for building:

```text
AI Agents
Agentic Workflows
Multi-Agent Systems
Enterprise AI Applications
Insurance Automation Systems
Production RAG Platforms
```

If LangChain helps you build AI applications, **LangGraph helps you orchestrate intelligent AI systems that can reason, collaborate, make decisions, and execute complex workflows.**