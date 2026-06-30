# CrewAI

## What is CrewAI?

CrewAI is an open-source framework used to build:

```text
AI Agents
Multi-Agent Systems
Autonomous Workflows
Agent Collaboration
AI Teams
```

CrewAI allows multiple AI agents to work together like a real team.

---

# Why CrewAI?

Traditional LLM Application:

```text
User
 ↓
LLM
 ↓
Response
```

---

CrewAI:

```text
User
 ↓
Agent Team
 ↓
Collaboration
 ↓
Response
```

---

# Real Example

Instead of one AI:

```text
One Agent
```

---

Use:

```text
Research Agent
Writer Agent
Reviewer Agent
```

working together.

---

# Core Idea

CrewAI models AI systems like:

```text
Human Teams
```

---

Example

Software Company

```text
Project Manager
Developer
Tester
```

---

CrewAI

```text
Planner Agent
Coder Agent
Reviewer Agent
```

---

# CrewAI Architecture

```text
User Query
      ↓
Crew
      ↓
Agent
      ↓
Task
      ↓
Agent
      ↓
Response
```

---

# Key Components

```text
Agents
Tasks
Crews
Tools
Processes
Memory
```

---

# 1. Agents

## What is an Agent?

An AI worker with:

```text
Role
Goal
Backstory
Tools
```

---

Example

Research Agent

```python
from crewai import Agent

researcher = Agent(

    role="Research Analyst",

    goal="Find accurate information",

    backstory="Expert researcher"
)
```

---

Agent Components

```text
Role
Goal
Tools
Memory
```

---

# Example

```text
Role:
Insurance Analyst

Goal:
Analyze policy documents

Backstory:
Expert in P&C insurance
```

---

# 2. Tasks

## What is a Task?

Work assigned to an agent.

---

Example

```python
from crewai import Task

task = Task(

    description="""
    Research collision coverage
    """,

    agent=researcher
)
```

---

Workflow

```text
Task
 ↓
Agent
 ↓
Output
```

---

# Example

```text
Task:
Find deductible information
```

---

Assigned To:

```text
Insurance Agent
```

---

# 3. Crew

## What is a Crew?

A team of agents.

---

Example

```python
from crewai import Crew

crew = Crew(

    agents=[

        researcher,

        writer
    ],

    tasks=[

        task1,

        task2
    ]
)
```

---

Visualization

```text
Research Agent
        ↓
Writer Agent
        ↓
Reviewer Agent
```

---

# Crew Workflow

```text
Crew
 ↓
Task Assignment
 ↓
Agent Collaboration
 ↓
Result
```

---

# Installation

```bash
pip install crewai
```

---

# First CrewAI Example

## Create Agents

```python
from crewai import Agent

researcher = Agent(

    role="Researcher",

    goal="Find AI information",

    backstory="Expert researcher"
)

writer = Agent(

    role="Writer",

    goal="Write reports",

    backstory="Professional writer"
)
```

---

# Create Tasks

```python
from crewai import Task

research_task = Task(

    description="""
    Research AI
    """,

    agent=researcher
)

write_task = Task(

    description="""
    Write report
    """,

    agent=writer
)
```

---

# Create Crew

```python
from crewai import Crew

crew = Crew(

    agents=[

        researcher,

        writer
    ],

    tasks=[

        research_task,

        write_task
    ]
)
```

---

# Run Crew

```python
result = crew.kickoff()

print(result)
```

---

# Output

```text
Research Completed
Report Generated
```

---

# 4. Tools

## What are Tools?

Functions agents can use.

---

Examples

```text
Search
Calculator
Database Query
API Calls
Python Execution
```

---

Example

```python
from crewai_tools import (
    SerperDevTool
)

search_tool = (
    SerperDevTool()
)
```

---

Agent With Tool

```python
researcher = Agent(

    role="Researcher",

    tools=[

        search_tool
    ]
)
```

---

Workflow

```text
Question
 ↓
Agent
 ↓
Tool
 ↓
Result
```

---

# 5. Processes

CrewAI supports:

```text
Sequential
Hierarchical
```

---

# Sequential Process

Tasks run one after another.

---

Example

```text
Research
    ↓
Write
    ↓
Review
```

---

# Hierarchical Process

Manager agent delegates work.

---

Example

```text
Manager
   ↓
Research Agent

Manager
   ↓
Writer Agent
```

---

Visualization

```text
Manager Agent
      ↓
Multiple Workers
```

---

# Example

```python
from crewai import Process

crew = Crew(

    process=Process.sequential
)
```

---

# Memory

CrewAI supports:

```text
Short-Term Memory
Long-Term Memory
Context Sharing
```

---

Benefits

```text
Better Collaboration
Persistent Knowledge
```

---

# Multi-Agent System Example

Research Team

```text
Research Agent
      ↓
Planner Agent
      ↓
Writer Agent
      ↓
Reviewer Agent
```

---

Workflow

```text
User Query
      ↓
Planner
      ↓
Research
      ↓
Writer
      ↓
Reviewer
      ↓
Response
```

---

# CrewAI + RAG

Architecture

```text
Question
      ↓
Retriever
      ↓
Documents
      ↓
Crew
      ↓
Answer
```

---

Example

```text
Retriever Agent
      ↓
Analysis Agent
      ↓
Response Agent
```

---

# CrewAI + LangChain

CrewAI can use:

```text
LangChain Tools
LangChain Retrievers
LangChain LLMs
```

---

Workflow

```text
LangChain
      ↓
CrewAI
      ↓
Multi-Agent System
```

---

# Insurance Claims Example

## FNOL Automation

Agents

```text
FNOL Agent

Coverage Agent

Fraud Agent

Severity Agent

Routing Agent
```

---

Workflow

```text
FNOL
 ↓
Coverage Verification
 ↓
Fraud Check
 ↓
Severity Prediction
 ↓
Routing
 ↓
Claims Handler
```

---

# Agent Collaboration Example

Coverage Agent

```text
Verify Policy
```

---

Fraud Agent

```text
Check Fraud Signals
```

---

Decision Agent

```text
Approve / Escalate
```

---

# Production Architecture

```text
User Query
      ↓
CrewAI
      ↓
Multiple Agents
      ↓
Tools
      ↓
Retriever
      ↓
LLM
      ↓
Response
```

---

# CrewAI vs LangGraph

| CrewAI | LangGraph |
|----------|----------|
| Role-Based | Workflow-Based |
| Easier Setup | More Flexible |
| Agent Teams | State Machines |
| Human Team Metaphor | Graph Metaphor |

---

# CrewAI vs LangChain

| CrewAI | LangChain |
|----------|----------|
| Multi-Agent Focus | General Framework |
| Team Collaboration | Chains & Tools |
| Autonomous Workflows | LLM Applications |

---

# CrewAI vs AutoGen

| CrewAI | AutoGen |
|----------|----------|
| Simpler | More Flexible |
| Role-Based Agents | Conversational Agents |
| Easier Learning Curve | More Complex |

---

# Advantages

```text
Easy Multi-Agent Development
Role-Based Design
Tool Integration
Memory Support
RAG Integration
```

---

# Limitations

```text
Less Control Than LangGraph
More Agent Overhead
Can Become Expensive
```

---

# Real Insurance Use Case

Knowledge Base

```text
Claims Policies
Coverage Rules
FNOL Documents
Fraud Guidelines
```

---

Pipeline

```text
User Claim
      ↓
FNOL Agent
      ↓
Coverage Agent
      ↓
Fraud Agent
      ↓
Severity Agent
      ↓
Decision Agent
      ↓
Claims Routing
```

---

# Interview Questions

### Q1. What is CrewAI?

```text
A framework for building collaborative multi-agent AI systems.
```

---

### Q2. What are the main components of CrewAI?

```text
Agents
Tasks
Crews
Tools
Processes
Memory
```

---

### Q3. What is a Crew?

```text
A team of AI agents working together to solve a problem.
```

---

### Q4. What is the difference between an Agent and a Task?

```text
An Agent performs work.

A Task defines the work to be done.
```

---

### Q5. Why is CrewAI popular?

```text
Because it simplifies building multi-agent AI applications.
```

---

# Learning Path

```text
LLM Fundamentals
      ↓
Prompt Engineering
      ↓
LangChain Basics
      ↓
Agents
      ↓
CrewAI
      ↓
Tasks
      ↓
Crews
      ↓
Tools
      ↓
Multi-Agent Systems
      ↓
Production AI Teams
```

# Most Important Topics for AI Engineers

```text
Agents
Tasks
Crews
Tools
Processes
Sequential Execution
Hierarchical Execution
Memory
RAG Integration
Multi-Agent Systems
```

CrewAI is one of the most practical frameworks for building:

```text
AI Teams
Autonomous Agents
Insurance Automation Systems
Research Assistants
Customer Support Agents
Enterprise AI Workflows
Multi-Agent Applications
```

For AI Engineers building collaborative AI systems, CrewAI provides one of the simplest and fastest ways to create production-ready **multi-agent architectures**.