# Tokenization

## What is Tokenization?

Tokenization is the process of breaking text into smaller units called **tokens**.

A token can be:

```text
Word
Sentence
Character
Subword
```

Tokenization is one of the most important preprocessing steps in Natural Language Processing (NLP).

---

# Why Do We Need Tokenization?

Computers cannot directly understand text.

Example:

```text
I love Machine Learning
```

For humans:

```text
Easy to Read
```

For computers:

```text
Just a String
```

Tokenization converts text into meaningful units that NLP models can process.

---

# Example

Sentence:

```text
I love Machine Learning
```

After Tokenization:

```python
[
    "I",
    "love",
    "Machine",
    "Learning"
]
```

These individual words become tokens.

---

# NLP Pipeline

```text
Raw Text
    ↓
Text Cleaning
    ↓
Tokenization
    ↓
Stopword Removal
    ↓
Lemmatization
    ↓
Vectorization
    ↓
Model Training
```

---

# Types of Tokenization

```text
Word Tokenization
Sentence Tokenization
Character Tokenization
Subword Tokenization
```

---

# 1. Word Tokenization

## Theory

Breaks text into individual words.

---

Example

Input:

```text
Machine Learning is Amazing
```

---

Output:

```python
[
 "Machine",
 "Learning",
 "is",
 "Amazing"
]
```

---

# Python Example

```python
text = "Machine Learning is Amazing"

tokens = text.split()

print(tokens)
```

Output:

```python
[
 'Machine',
 'Learning',
 'is',
 'Amazing'
]
```

---

# Real Example

Sentence:

```text
Customer vehicle damaged in accident
```

Tokens:

```python
[
 'Customer',
 'vehicle',
 'damaged',
 'in',
 'accident'
]
```

---

# 2. Sentence Tokenization

## Theory

Splits a paragraph into individual sentences.

---

Example

Input:

```text
I love NLP.
Machine Learning is amazing.
```

---

Output:

```python
[
 "I love NLP.",
 "Machine Learning is amazing."
]
```

---

# NLTK Example

```python
from nltk.tokenize import sent_tokenize

text = """
I love NLP.
Machine Learning is amazing.
"""

sentences = sent_tokenize(text)

print(sentences)
```

---

Output:

```python
[
 "I love NLP.",
 "Machine Learning is amazing."
]
```

---

# Applications

```text
Document Summarization
Question Answering
Chatbots
```

---

# 3. Character Tokenization

## Theory

Breaks text into characters.

---

Input:

```text
NLP
```

---

Output:

```python
[
 'N',
 'L',
 'P'
]
```

---

Python Example

```python
text = "NLP"

chars = list(text)

print(chars)
```

---

Output:

```python
[
 'N',
 'L',
 'P'
]
```

---

# Applications

```text
OCR
Language Modeling
Spell Checking
```

---

# 4. Subword Tokenization

## Theory

Breaks words into smaller meaningful pieces.

---

Why?

Many words may be rare or unseen.

Example:

```text
unhappiness
```

---

Subword Tokens:

```text
un
happy
ness
```

---

Benefits:

```text
Smaller Vocabulary
Handle Unknown Words
Better Generalization
```

---

# Example

Word:

```text
playing
```

Subwords:

```text
play
ing
```

---

# Used In

```text
BERT
GPT
Llama
Claude
Gemini
```

---

# Tokenization in LLMs

Modern LLMs do not process words directly.

They process:

```text
Tokens
```

---

Example

Text:

```text
I love AI
```

May become:

```text
[101, 205, 786]
```

---

The model only sees numbers.

---

# GPT Tokenization Example

Word:

```text
ChatGPT
```

Possible Tokens:

```text
Chat

GPT
```

---

Word:

```text
unbelievable
```

Possible Tokens:

```text
un

believ

able
```

---

# Why LLMs Use Subword Tokenization?

Advantages:

```text
Smaller Vocabulary

Better Memory Usage

Handles New Words

Efficient Training
```

---

# Popular Tokenization Algorithms

```text
Byte Pair Encoding (BPE)
WordPiece
SentencePiece
tiktoken
```

---

# 1. Byte Pair Encoding (BPE)

Used by:

```text
GPT Models
OpenAI Models
```

---

Example

Word:

```text
playing
```

↓

```text
play
ing
```

---

Benefits:

```text
Efficient
Widely Used
```

---

# 2. WordPiece

Used by:

```text
BERT
```

---

Example

```text
unhappiness
```

↓

```text
un
happy
ness
```

---

# 3. SentencePiece

Used by:

```text
T5
Llama
Many Open Source LLMs
```

---

Works directly on raw text.

---

# Token IDs

Models don't understand words.

Example:

```text
Machine Learning
```

↓

```python
[
 254,
 1200
]
```

These are called:

```text
Token IDs
```

---

# Padding

## Theory

Sentences have different lengths.

Example:

```text
I love NLP
```

Tokens:

```text
3
```

---

Sentence:

```text
I love Machine Learning and AI
```

Tokens:

```text
6
```

---

Need equal lengths.

Solution:

```text
Padding
```

---

Example:

```python
[
 1,
 2,
 3,
 0,
 0
]
```

---

# Truncation

## Theory

Cuts very long sequences.

---

Example:

```text
Maximum Length = 512
```

Input:

```text
1000 Tokens
```

---

Output:

```text
First 512 Tokens
```

---

# Special Tokens

Modern NLP models use special tokens.

---

Examples:

```text
[CLS]

[SEP]

[PAD]

[MASK]

<EOS>

<BOS>
```

---

Purpose:

```text
Classification
Separation
Padding
Masking
```

---

# Tokenization Example with Transformers

```python
from transformers import AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained(
    "bert-base-uncased"
)

tokens = tokenizer.tokenize(
    "I love NLP"
)

print(tokens)
```

---

Output:

```python
[
 'i',
 'love',
 'nlp'
]
```

---

# Insurance Example

Claim Note:

```text
Customer vehicle damaged during collision.
```

---

Word Tokens:

```python
[
 'customer',
 'vehicle',
 'damaged',
 'during',
 'collision'
]
```

---

Used For:

```text
Claim Classification
Fraud Detection
Claim Routing
Severity Prediction
```

---

# Advantages of Tokenization

```text
Transforms Text into Processable Units
Reduces Complexity
Enables NLP Modeling
Improves Understanding
```

---

# Challenges

```text
Unknown Words
Misspellings
Multiple Languages
Large Vocabulary
```

---

# Interview Questions

### Q1. What is Tokenization?

```text
The process of splitting text into smaller units called tokens.
```

---

### Q2. Why is Tokenization important?

```text
Because machine learning models cannot directly process raw text.
```

---

### Q3. What are the types of Tokenization?

```text
Word
Sentence
Character
Subword
```

---

### Q4. Which tokenization method is used by LLMs?

```text
Subword Tokenization
```

---

### Q5. What is BPE?

```text
Byte Pair Encoding, a popular tokenization algorithm used by GPT models.
```

---

# Learning Path

```text
Text Processing
      ↓
Tokenization
      ↓
Word Tokenization
      ↓
Sentence Tokenization
      ↓
Character Tokenization
      ↓
Subword Tokenization
      ↓
BPE
      ↓
WordPiece
      ↓
SentencePiece
      ↓
Transformers
      ↓
LLMs
```

# Most Important Topics for AI Engineers

```text
Word Tokenization
Sentence Tokenization
Subword Tokenization
BPE
WordPiece
SentencePiece
Token IDs
Padding
Truncation
Special Tokens
```

Tokenization is the foundation of modern NLP systems and is used in:

```text
BERT
GPT
Llama
Claude
Gemini
RAG Systems
Chatbots
Search Engines
Agentic AI
```

Before any Transformer or LLM can understand text, it must first convert that text into tokens through tokenization.