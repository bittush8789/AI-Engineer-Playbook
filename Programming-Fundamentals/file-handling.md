# File Handling in Python

## What is File Handling?

File Handling is the process of:

- Creating files
- Reading files
- Writing files
- Updating files
- Deleting files

Python provides built-in functions to work with files.

---

## Why File Handling?

Applications need to store data permanently.

Examples:

```text
Customer Records
Claim Data
Policy Information
Logs
Model Outputs
Configuration Files
```

Without file handling, data is lost when the program stops.

---

# File Types

## Text Files

Examples:

```text
.txt
.csv
.json
.md
```

---

## Binary Files

Examples:

```text
.jpg
.png
.pdf
.pkl
```

---

# File Handling Workflow

```text
Open File
    │
    ▼
Read / Write
    │
    ▼
Close File
```

---

# Opening a File

## Syntax

```python
file = open("filename", "mode")
```

---

## Parameters

### Filename

```python
"data.txt"
```

---

### Mode

```text
r  → Read
w  → Write
a  → Append
x  → Create
rb → Read Binary
wb → Write Binary
```

---

# 1. Read Mode (r)

## Theory

Used to read an existing file.

If file doesn't exist:

```text
FileNotFoundError
```

---

## Example

data.txt

```text
Hello AI Engineer
```

---

Python

```python
file = open("data.txt", "r")

content = file.read()

print(content)

file.close()
```

### Output

```text
Hello AI Engineer
```

---

# Understanding read()

## Theory

Reads entire file content.

---

## Example

```python
file = open("data.txt", "r")

print(file.read())
```

---

# 2. Write Mode (w)

## Theory

Creates a new file.

If file already exists:

```text
Existing content is overwritten.
```

---

## Example

```python
file = open("data.txt", "w")

file.write("Hello Python")

file.close()
```

---

### File Content

```text
Hello Python
```

---

# 3. Append Mode (a)

## Theory

Adds content at the end of a file.

Does not remove existing content.

---

## Example

```python
file = open("data.txt", "a")

file.write("\nWelcome AI")

file.close()
```

---

### File Content

```text
Hello Python
Welcome AI
```

---

# 4. Create Mode (x)

## Theory

Creates a file only if it doesn't already exist.

---

## Example

```python
file = open(
    "newfile.txt",
    "x"
)

file.close()
```

---

# Reading Methods

# read()

## Theory

Reads entire file.

---

## Example

```python
file = open("data.txt", "r")

print(file.read())
```

---

# readline()

## Theory

Reads one line at a time.

---

## Example

```python
file = open("data.txt", "r")

print(file.readline())
```

---

### Output

```text
Hello Python
```

---

# readlines()

## Theory

Returns all lines as a list.

---

## Example

```python
file = open("data.txt", "r")

print(file.readlines())
```

---

### Output

```python
[
'Hello Python\n',
'Welcome AI'
]
```

---

# Using Loops

## Example

```python
file = open("data.txt", "r")

for line in file:

    print(line)

file.close()
```

---

# Closing Files

## Theory

Always close files after use.

---

## Example

```python
file = open("data.txt", "r")

print(file.read())

file.close()
```

---

# Problem with close()

If exception occurs:

```text
File may remain open.
```

---

# Using with Statement

## Recommended Method

Automatically closes file.

---

## Example

```python
with open("data.txt", "r") as file:

    print(file.read())
```

---

## Advantages

- Cleaner Code
- Automatic Close
- Safer

---

# Writing Using with

```python
with open("data.txt", "w") as file:

    file.write("Hello AI")
```

---

# File Exists Check

## Example

```python
import os

if os.path.exists("data.txt"):

    print("File Exists")

else:

    print("File Not Found")
```

---

# Delete File

## Example

```python
import os

os.remove("data.txt")
```

---

# Exception Handling with Files

## Example

```python
try:

    with open(
        "data.txt",
        "r"
    ) as file:

        print(file.read())

except FileNotFoundError:

    print("File Not Found")
```

---

# Working with CSV Files

## Theory

CSV = Comma Separated Values

---

employees.csv

```csv
Name,Age
Bittu,25
Rahul,24
```

---

## Read CSV

```python
import csv

with open(
    "employees.csv",
    "r"
) as file:

    reader = csv.reader(file)

    for row in reader:

        print(row)
```

---

### Output

```python
['Name', 'Age']
['Bittu', '25']
['Rahul', '24']
```

---

# Writing CSV

```python
import csv

with open(
    "employees.csv",
    "w",
    newline=""
) as file:

    writer = csv.writer(file)

    writer.writerow(
        ["Name", "Age"]
    )

    writer.writerow(
        ["Bittu", 25]
    )
```

---

# Working with JSON Files

## Theory

JSON is widely used for APIs and AI applications.

---

sample.json

```json
{
  "name": "Bittu",
  "age": 25
}
```

---

## Read JSON

```python
import json

with open(
    "sample.json",
    "r"
) as file:

    data = json.load(file)

print(data)
```

---

### Output

```python
{
'name':'Bittu',
'age':25
}
```

---

# Write JSON

```python
import json

data = {
    "name": "Bittu",
    "age": 25
}

with open(
    "sample.json",
    "w"
) as file:

    json.dump(
        data,
        file,
        indent=4
    )
```

---

# Binary Files

## Example

```python
with open(
    "image.jpg",
    "rb"
) as file:

    data = file.read()
```

---

# Real AI Example 1

## Save Model Predictions

```python
prediction = "High Severity"

with open(
    "prediction.txt",
    "w"
) as file:

    file.write(prediction)
```

---

# Real AI Example 2

## Store Chat History

```python
chat = "User: Hello"

with open(
    "chat.txt",
    "a"
) as file:

    file.write(
        chat + "\n"
    )
```

---

# Real AI Example 3

## Read Training Data

```python
import pandas as pd

df = pd.read_csv(
    "claims.csv"
)

print(df.head())
```

---

# Real Insurance Example

## Store Claim Information

```python
claim = {
    "claim_id": 101,
    "amount": 50000,
    "status": "Open"
}

import json

with open(
    "claim.json",
    "w"
) as file:

    json.dump(
        claim,
        file
    )
```

---

# File Modes Summary

| Mode | Meaning |
|--------|---------|
| r | Read |
| w | Write |
| a | Append |
| x | Create |
| rb | Read Binary |
| wb | Write Binary |

---

# Best Practices

## Use with Statement

✅ Good

```python
with open(...)
```

---

## Handle Exceptions

```python
try:
    ...
except:
    ...
```

---

## Close Files Properly

Avoid resource leaks.

---

## Use JSON for Structured Data

Better than plain text.

---

# Interview Questions

### Q1. What is File Handling?

```text
The process of reading, writing, creating, and managing files.
```

---

### Q2. Difference between w and a?

```text
w → Overwrites file

a → Appends content
```

---

### Q3. Why use with?

```text
Automatically closes files.
```

---

### Q4. Difference between read() and readline()?

```text
read() → Entire file

readline() → One line
```

---

### Q5. What is JSON?

```text
A lightweight data interchange format.
```

---

# Learning Path

```text
Open File
   ↓
Read File
   ↓
Write File
   ↓
Append File
   ↓
with Statement
   ↓
Exception Handling
   ↓
CSV Files
   ↓
JSON Files
   ↓
Binary Files
   ↓
Production File Processing
```

# File Handling for AI Engineers

Most common use cases:

```text
Dataset Processing
Model Artifacts
Prompt Storage
Configuration Files
Logs
Chat History
JSON APIs
CSV Datasets
PDF Processing
Document Ingestion
```

File Handling is heavily used in:

```text
Machine Learning
MLOps
LLMOps
RAG Systems
FastAPI
LangChain
LangGraph
Agentic AI
AI Platform Engineering
```