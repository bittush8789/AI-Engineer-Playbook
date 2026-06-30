# Data Structures & Algorithms (DSA)

## What are Data Structures?

A Data Structure is a way of organizing, storing, and managing data so it can be used efficiently.

Think of it as a container for data.

Examples:

```text
List
Dictionary
Stack
Queue
Tree
Graph
```

---

## What are Algorithms?

An Algorithm is a step-by-step procedure to solve a problem.

Examples:

```text
Searching
Sorting
Path Finding
Recommendation
Optimization
```

---

# Why DSA is Important?

Benefits:

- Faster Programs
- Better Memory Usage
- Efficient Data Processing
- Better Problem Solving
- Required for Interviews
- Used in AI Systems

---

# DSA Roadmap

```text
Arrays
   ↓
Strings
   ↓
Linked Lists
   ↓
Stacks
   ↓
Queues
   ↓
Hash Tables
   ↓
Recursion
   ↓
Trees
   ↓
Heaps
   ↓
Graphs
   ↓
Sorting
   ↓
Searching
   ↓
Dynamic Programming
```

---

# 1. Arrays (Lists in Python)

## Theory

An array stores multiple values in contiguous memory locations.

Python uses Lists.

---

## Example

```python
numbers = [10, 20, 30, 40]

print(numbers)
```

Output:

```text
[10, 20, 30, 40]
```

---

## Access Elements

```python
print(numbers[0])
```

Output:

```text
10
```

---

## Time Complexity

| Operation | Complexity |
|------------|------------|
| Access | O(1) |
| Search | O(n) |
| Insert End | O(1) |
| Insert Middle | O(n) |
| Delete | O(n) |

---

# 2. Strings

## Theory

A string is a sequence of characters.

---

## Example

```python
name = "Bittu"

print(name)
```

---

## Reverse String

```python
name = "Bittu"

print(name[::-1])
```

Output:

```text
uttiB
```

---

## Time Complexity

| Operation | Complexity |
|------------|------------|
| Access | O(1) |
| Search | O(n) |

---

# 3. Linked List

## Theory

A linked list stores elements using nodes.

Each node contains:

```text
Data
Pointer to Next Node
```

---

## Structure

```text
10 → 20 → 30 → 40
```

---

## Node Example

```python
class Node:

    def __init__(self, data):
        self.data = data
        self.next = None
```

---

## Advantages

- Dynamic Size
- Easy Insertions

---

## Disadvantages

- Extra Memory
- Slow Access

---

## Time Complexity

| Operation | Complexity |
|------------|------------|
| Access | O(n) |
| Search | O(n) |
| Insert | O(1) |

---

# 4. Stack

## Theory

A Stack follows:

```text
LIFO
Last In First Out
```

Example:

```text
Books Stack
```

---

## Operations

```text
Push
Pop
Peek
```

---

## Example

```python
stack = []

stack.append(10)
stack.append(20)

print(stack.pop())
```

Output:

```text
20
```

---

## Time Complexity

| Operation | Complexity |
|------------|------------|
| Push | O(1) |
| Pop | O(1) |

---

# 5. Queue

## Theory

A Queue follows:

```text
FIFO
First In First Out
```

Example:

```text
Ticket Counter
```

---

## Example

```python
from collections import deque

queue = deque()

queue.append(10)
queue.append(20)

print(queue.popleft())
```

Output:

```text
10
```

---

## Time Complexity

| Operation | Complexity |
|------------|------------|
| Enqueue | O(1) |
| Dequeue | O(1) |

---

# 6. Hash Table (Dictionary)

## Theory

Stores data using:

```text
Key → Value
```

Python Dictionary uses hashing.

---

## Example

```python
employee = {
    "name": "Bittu",
    "age": 25
}

print(employee["name"])
```

Output:

```text
Bittu
```

---

## Time Complexity

| Operation | Complexity |
|------------|------------|
| Search | O(1) |
| Insert | O(1) |
| Delete | O(1) |

---

# 7. Recursion

## Theory

A function calling itself.

---

## Example

Factorial:

```python
def factorial(n):

    if n == 1:
        return 1

    return n * factorial(n - 1)

print(factorial(5))
```

Output:

```text
120
```

---

## Use Cases

- Trees
- Graphs
- Backtracking
- Dynamic Programming

---

# 8. Trees

## Theory

A hierarchical data structure.

---

## Structure

```text
       10
      /  \
     20   30
```

---

## Terminology

```text
Root
Child
Parent
Leaf
```

---

## Example Node

```python
class TreeNode:

    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None
```

---

## AI Use Cases

- Decision Trees
- Random Forest
- Search Systems

---

# 9. Binary Search Tree (BST)

## Theory

A special tree where:

```text
Left < Root
Right > Root
```

---

## Example

```text
      50
     /  \
   25    75
```

---

## Time Complexity

| Operation | Complexity |
|------------|------------|
| Search | O(log n) |
| Insert | O(log n) |

---

# 10. Heap

## Theory

A tree used for priority management.

---

## Types

### Max Heap

Largest element at top.

---

### Min Heap

Smallest element at top.

---

## Example

```python
import heapq

heap = [5, 3, 8]

heapq.heapify(heap)

print(heapq.heappop(heap))
```

Output:

```text
3
```

---

## AI Use Cases

- Task Scheduling
- Priority Queues
- Search Algorithms

---

# 11. Graphs

## Theory

A graph consists of:

```text
Nodes
Edges
```

---

## Example

```text
A ---- B
|      |
C ---- D
```

---

## Applications

- Social Networks
- Knowledge Graphs
- Recommendation Systems
- Route Planning

---

## Graph Representation

```python
graph = {
    "A": ["B", "C"],
    "B": ["D"]
}
```

---

# 12. Searching Algorithms

## Linear Search

### Theory

Check every element one by one.

---

### Example

```python
numbers = [10, 20, 30, 40]

target = 30

for num in numbers:

    if num == target:
        print("Found")
```

---

### Complexity

```text
O(n)
```

---

# Binary Search

## Theory

Works on sorted arrays.

Repeatedly divide search space.

---

## Example

```python
def binary_search(arr, target):

    left = 0
    right = len(arr) - 1

    while left <= right:

        mid = (left + right) // 2

        if arr[mid] == target:
            return mid

        elif arr[mid] < target:
            left = mid + 1

        else:
            right = mid - 1

    return -1
```

---

## Complexity

```text
O(log n)
```

---

# 13. Sorting Algorithms

## Bubble Sort

### Theory

Repeatedly swap adjacent elements.

---

### Example

```python
arr = [5, 2, 8, 1]

for i in range(len(arr)):

    for j in range(len(arr)-1):

        if arr[j] > arr[j+1]:

            arr[j], arr[j+1] = arr[j+1], arr[j]
```

---

### Complexity

```text
O(n²)
```

---

# Python Built-in Sorting

```python
numbers = [5, 2, 8, 1]

numbers.sort()

print(numbers)
```

Output:

```text
[1, 2, 5, 8]
```

---

# 14. Dynamic Programming (DP)

## Theory

A technique that solves problems by storing previously computed results.

---

## Example

Fibonacci:

### Normal

```text
Repeated Calculations
```

---

### DP

```python
memo = {}

def fib(n):

    if n in memo:
        return memo[n]

    if n <= 2:
        return 1

    memo[n] = fib(n-1) + fib(n-2)

    return memo[n]
```

---

## Benefits

- Faster Execution
- Avoids Recalculation

---

# Time Complexity Cheat Sheet

| Data Structure | Access | Search | Insert | Delete |
|---------------|---------|---------|---------|---------|
| Array | O(1) | O(n) | O(n) | O(n) |
| Linked List | O(n) | O(n) | O(1) | O(1) |
| Stack | O(n) | O(n) | O(1) | O(1) |
| Queue | O(n) | O(n) | O(1) | O(1) |
| Hash Table | O(1) | O(1) | O(1) | O(1) |
| BST | O(log n) | O(log n) | O(log n) | O(log n) |
| Heap | O(n) | O(n) | O(log n) | O(log n) |

---

# DSA for AI Engineers

## Most Important Topics

```text
Arrays
Strings
Hash Tables
Stacks
Queues
Trees
Graphs
Searching
Sorting
Recursion
```

---

## Important for Agentic AI

```text
Graphs
Trees
Priority Queues
Hash Maps
```

---

## Important for RAG Systems

```text
Hash Tables
Graphs
Searching
Heaps
```

---

## Important for AI Platform Engineers

```text
Arrays
Hash Maps
Queues
Heaps
Graphs
Distributed Algorithms
```

---

# Learning Path

```text
Arrays
   ↓
Strings
   ↓
Hash Tables
   ↓
Stacks
   ↓
Queues
   ↓
Recursion
   ↓
Linked Lists
   ↓
Trees
   ↓
BST
   ↓
Heaps
   ↓
Graphs
   ↓
Searching
   ↓
Sorting
   ↓
Dynamic Programming
```

# Recommendation for AI Engineers

Focus heavily on:

```text
Arrays
Strings
Hash Tables
Queues
Trees
Graphs
Searching
Sorting
```

These topics are sufficient for most AI Engineer, MLOps Engineer, AI Platform Engineer, and FDE interviews while also helping build scalable AI systems.