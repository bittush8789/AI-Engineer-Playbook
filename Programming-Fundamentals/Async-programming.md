# Async Programming in Python

## What is Async Programming?

Async Programming (Asynchronous Programming) is a programming technique that allows multiple tasks to run concurrently without waiting for each task to finish before starting the next one.

---

## Why Async Programming?

### Synchronous Execution

Tasks run one after another.

```text
Task 1
   ↓
Task 2
   ↓
Task 3
```

If one task takes 5 seconds, everything else waits.

---

### Asynchronous Execution

Tasks can run concurrently.

```text
Task 1 ──┐
Task 2 ──┼── Running Together
Task 3 ──┘
```

Result:

```text
Faster Applications
Better Resource Usage
Higher Throughput
```

---

# Real-World Example

Imagine ordering food.

### Synchronous

```text
Order Food
Wait 30 Minutes
Eat
```

Nothing else happens while waiting.

---

### Asynchronous

```text
Order Food
Study
Watch Movie
Food Arrives
Eat
```

You utilize waiting time efficiently.

---

# Why Async Matters for AI Engineers?

AI applications often wait for:

```text
API Calls
Database Queries
LLM Responses
File Uploads
Network Requests
```

Instead of blocking the application, async allows handling many requests simultaneously.

---

# Synchronous Example

```python
import time

def task():

    print("Started")

    time.sleep(3)

    print("Completed")

task()
```

---

### Output

```text
Started

(wait 3 seconds)

Completed
```

Program is blocked for 3 seconds.

---

# Async Keywords

Python async programming uses:

```python
async
await
asyncio
```

---

# 1. async Function

## Theory

An async function is declared using:

```python
async def
```

---

## Example

```python
async def hello():

    print("Hello")
```

---

# 2. await Keyword

## Theory

`await` pauses execution until a task completes.

Used inside async functions.

---

## Example

```python
import asyncio

async def hello():

    await asyncio.sleep(2)

    print("Hello")

asyncio.run(hello())
```

---

### Output

```text
(wait 2 seconds)

Hello
```

---

# asyncio Module

## Theory

Python's built-in library for asynchronous programming.

---

## Example

```python
import asyncio

async def main():

    print("Async Program")

asyncio.run(main())
```

---

# Synchronous vs Async Example

## Synchronous

```python
import time

def task1():

    time.sleep(2)

    print("Task 1")


def task2():

    time.sleep(2)

    print("Task 2")


task1()
task2()
```

---

### Execution Time

```text
4 Seconds
```

---

## Asynchronous

```python
import asyncio

async def task1():

    await asyncio.sleep(2)

    print("Task 1")


async def task2():

    await asyncio.sleep(2)

    print("Task 2")


async def main():

    await asyncio.gather(
        task1(),
        task2()
    )

asyncio.run(main())
```

---

### Execution Time

```text
2 Seconds
```

Both tasks run concurrently.

---

# asyncio.gather()

## Theory

Runs multiple async tasks concurrently.

---

## Example

```python
import asyncio

async def task1():

    await asyncio.sleep(1)

    print("Task 1")


async def task2():

    await asyncio.sleep(1)

    print("Task 2")


async def main():

    await asyncio.gather(
        task1(),
        task2()
    )

asyncio.run(main())
```

---

### Output

```text
Task 1
Task 2
```

---

# Multiple API Calls Example

## Synchronous

```python
API 1 → 2 sec
API 2 → 2 sec
API 3 → 2 sec
```

Total:

```text
6 Seconds
```

---

## Async

```python
API 1
API 2
API 3
```

Run together.

Total:

```text
2 Seconds
```

---

# Async HTTP Requests

Install:

```bash
pip install aiohttp
```

---

## Example

```python
import aiohttp
import asyncio

async def fetch():

    async with aiohttp.ClientSession() as session:

        async with session.get(
            "https://example.com"
        ) as response:

            print(
                await response.text()
            )

asyncio.run(fetch())
```

---

# Async File Operations

Install:

```bash
pip install aiofiles
```

---

## Example

```python
import aiofiles
import asyncio

async def read_file():

    async with aiofiles.open(
        "data.txt",
        "r"
    ) as file:

        content = await file.read()

        print(content)

asyncio.run(read_file())
```

---

# Async Database Operations

Example:

```python
async def get_users():

    users = await db.fetch_all()

    return users
```

---

# Async in FastAPI

## Why FastAPI Uses Async?

FastAPI is built on:

```text
ASGI
Async IO
```

which supports thousands of concurrent requests.

---

## Synchronous Endpoint

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")

def home():

    return {
        "message": "Hello"
    }
```

---

## Async Endpoint

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")

async def home():

    return {
        "message": "Hello"
    }
```

---

## Benefits

```text
Higher Throughput
Better Performance
Scalability
```

---

# Real AI Example 1

## Multiple LLM Calls

```python
import asyncio

async def call_model():

    await asyncio.sleep(2)

    return "Response"


async def main():

    responses = await asyncio.gather(
        call_model(),
        call_model(),
        call_model()
    )

    print(responses)

asyncio.run(main())
```

---

# Real AI Example 2

## RAG Retrieval

```python
async def retrieve():

    docs = await vector_db.search()

    return docs
```

---

# Real AI Example 3

## Multi-Agent Systems

```python
Planner Agent
      │
      ▼
Research Agent

Coder Agent

Reviewer Agent
```

All agents can execute concurrently.

---

# Insurance Example

## FNOL Automation

```text
Customer Submits Claim
           │
           ▼
Coverage Check

Fraud Detection

Severity Prediction
```

All services can run asynchronously.

---

# Async vs Multithreading

| Async | Multithreading |
|---------|---------|
| Single Thread | Multiple Threads |
| Best for I/O | Best for CPU Tasks |
| Lightweight | Heavier |
| FastAPI Uses Async | Parallel Computation |

---

# Async vs Multiprocessing

| Async | Multiprocessing |
|---------|---------|
| One Process | Multiple Processes |
| I/O Bound | CPU Bound |
| Lightweight | High Resource Usage |

---

# When to Use Async?

Use Async For:

```text
API Calls
Databases
WebSockets
LLM Calls
RAG Systems
Agent Systems
File Uploads
```

---

# When NOT to Use Async?

Avoid Async For:

```text
Heavy ML Training
Image Processing
Large Matrix Computation
Deep Learning Training
```

Use:

```text
Multiprocessing
Ray
Spark
GPU Computing
```

---

# Common Async Libraries

## Built-in

```python
asyncio
```

---

## HTTP

```python
aiohttp
httpx
```

---

## Files

```python
aiofiles
```

---

## Database

```python
asyncpg
motor
```

---

# Interview Questions

### Q1. What is Async Programming?

```text
A programming model that allows tasks to run concurrently without blocking execution.
```

---

### Q2. Difference between async and await?

```text
async:
Defines async function.

await:
Waits for async task completion.
```

---

### Q3. What is asyncio?

```text
Python's asynchronous programming framework.
```

---

### Q4. What is asyncio.gather()?

```text
Runs multiple async tasks concurrently.
```

---

### Q5. When should you use async?

```text
API Calls
Database Queries
Network Operations
```

---

# Learning Path

```text
async
   ↓
await
   ↓
asyncio
   ↓
asyncio.gather()
   ↓
aiohttp
   ↓
aiofiles
   ↓
FastAPI Async
   ↓
Async Databases
   ↓
LLM APIs
   ↓
Agent Systems
```

# Async Programming for AI Engineers

Most important use cases:

```text
FastAPI APIs
OpenAI APIs
RAG Systems
LangChain
LangGraph
Multi-Agent Systems
Vector Databases
WebSockets
Real-Time AI Applications
```

Mastering Async Programming is essential for building scalable AI APIs, RAG platforms, Agentic AI systems, AI copilots, and production-grade AI infrastructure.