# Text Processing in NLP

## What is NLP?

NLP stands for:

```text
Natural Language Processing
```

It is a branch of AI that enables computers to understand, process, analyze, and generate human language.

---

## Examples of NLP Applications

```text
ChatGPT
Google Translate
Sentiment Analysis
Spam Detection
Chatbots
Voice Assistants
Search Engines
```

---

# What is Text Processing?

Text Processing is the first step in every NLP pipeline.

Raw text from humans is usually:

```text
Unstructured
Noisy
Inconsistent
```

Text Processing converts raw text into a clean format that Machine Learning and Deep Learning models can understand.

---

# Why Text Processing?

Example:

Raw Text:

```text
"Hello!!! I am learning NLP in 2026 :)"
```

Problems:

```text
Special Characters
Numbers
Extra Spaces
Punctuation
Emojis
```

---

After Processing:

```text
hello learning nlp
```

This cleaned text is easier for NLP models to learn from.

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
Stemming/Lemmatization
    ↓
Vectorization
    ↓
Machine Learning Model
```

---

# Step 1: Text Cleaning

## Theory

Remove unnecessary information from text.

---

Example

Raw:

```text
"Hello!!! NLP is Awesome :)"
```

---

Cleaned:

```text
hello nlp is awesome
```

---

# Convert to Lowercase

Why?

```text
Dog
DOG
dog
```

should be treated as the same word.

---

Example

```python
text = "Machine Learning"

print(
    text.lower()
)
```

Output:

```text
machine learning
```

---

# Remove Punctuation

Example

Input:

```text
Hello!!!
```

Output:

```text
Hello
```

---

Python Example

```python
import re

text = "Hello!!!"

clean = re.sub(
    r"[^\w\s]",
    "",
    text
)

print(clean)
```

---

# Remove Numbers

Input:

```text
AI 2026
```

Output:

```text
AI
```

---

Example

```python
import re

text = "AI 2026"

clean = re.sub(
    r"\d+",
    "",
    text
)

print(clean)
```

---

# Remove Extra Spaces

Input:

```text
I     love     NLP
```

Output:

```text
I love NLP
```

---

Example

```python
text = "I     love NLP"

clean = " ".join(
    text.split()
)

print(clean)
```

---

# Step 2: Tokenization

## Theory

Tokenization breaks text into smaller units called tokens.

---

Sentence:

```text
I love Machine Learning
```

---

Tokens:

```text
I
love
Machine
Learning
```

---

Python Example

```python
text = "I love NLP"

tokens = text.split()

print(tokens)
```

Output:

```python
['I', 'love', 'NLP']
```

---

# Types of Tokenization

## Word Tokenization

```text
Machine Learning is Amazing
```

↓

```text
["Machine","Learning","is","Amazing"]
```

---

## Sentence Tokenization

```text
Hello World.
I Love NLP.
```

↓

```text
[
 "Hello World.",
 "I Love NLP."
]
```

---

## Character Tokenization

```text
NLP
```

↓

```text
['N','L','P']
```

---

# Step 3: Stopword Removal

## Theory

Stopwords are very common words that usually carry little meaning.

Examples:

```text
is
am
are
the
a
an
of
to
in
```

---

Sentence:

```text
I am learning NLP
```

---

After Stopword Removal:

```text
learning NLP
```

---

Python Example

```python
from nltk.corpus import stopwords

stop_words = set(
    stopwords.words("english")
)

words = [
    word
    for word in tokens
    if word not in stop_words
]
```

---

# Why Remove Stopwords?

Benefits:

```text
Less Noise
Smaller Vocabulary
Faster Training
```

---

# Step 4: Stemming

## Theory

Reduce words to their root form.

---

Examples:

```text
playing
played
plays
```

↓

```text
play
```

---

Python Example

```python
from nltk.stem import PorterStemmer

stemmer = PorterStemmer()

print(
    stemmer.stem(
        "playing"
    )
)
```

Output:

```text
play
```

---

# Stemming Issues

Sometimes results are not real words.

Example:

```text
studies
```

↓

```text
studi
```

---

# Step 5: Lemmatization

## Theory

Converts words into meaningful dictionary forms.

---

Examples:

```text
running
```

↓

```text
run
```

---

```text
better
```

↓

```text
good
```

---

Python Example

```python
from nltk.stem import WordNetLemmatizer

lemmatizer = WordNetLemmatizer()

print(
    lemmatizer.lemmatize(
        "running",
        pos="v"
    )
)
```

Output:

```text
run
```

---

# Stemming vs Lemmatization

| Stemming | Lemmatization |
|-----------|-----------|
| Faster | Slower |
| Less Accurate | More Accurate |
| May Produce Invalid Words | Produces Valid Words |

---

# Step 6: Text Normalization

## Theory

Standardize text representation.

---

Example

Input:

```text
U.S.A
USA
usa
```

Output:

```text
usa
```

---

Benefits:

```text
Consistency
Better Learning
```

---

# Step 7: Vectorization

Machines cannot understand text directly.

Need conversion:

```text
Text
 ↓
Numbers
```

---

Example

```text
I love NLP
```

↓

```text
[1,0,1,1]
```

---

Methods:

```text
Bag of Words
TF-IDF
Word Embeddings
```

---

# Complete Example

Raw Text:

```text
"Machine Learning is AWESOME!!!"
```

---

Lowercase:

```text
machine learning is awesome
```

---

Tokenization:

```text
[
 "machine",
 "learning",
 "is",
 "awesome"
]
```

---

Remove Stopwords:

```text
[
 "machine",
 "learning",
 "awesome"
]
```

---

Lemmatization:

```text
[
 "machine",
 "learn",
 "awesome"
]
```

---

Vectorization:

```text
[0.3,0.7,0.2]
```

---

# Real-World NLP Example

## Insurance Claims

Claim Notes:

```text
Customer vehicle damaged due to collision.
```

---

Processing:

```text
Lowercase
Tokenization
Stopword Removal
Lemmatization
```

---

Output:

```text
customer
vehicle
damage
collision
```

---

Used For:

```text
Fraud Detection
Claim Classification
Severity Prediction
```

---

# Libraries for Text Processing

## NLTK

:contentReference[oaicite:0]{index=0}

Used for:

```text
Tokenization
Stemming
Lemmatization
Stopwords
```

---

## spaCy

:contentReference[oaicite:1]{index=1}

Used for:

```text
Industrial NLP
NER
POS Tagging
Parsing
```

---

## Transformers

:contentReference[oaicite:2]{index=2}

Used for:

```text
LLMs
Embeddings
Modern NLP
```

---

# Interview Questions

### Q1. What is Text Processing?

```text
The process of cleaning and preparing raw text data for NLP models.
```

---

### Q2. What is Tokenization?

```text
Breaking text into smaller units called tokens.
```

---

### Q3. What are Stopwords?

```text
Common words that often carry little semantic meaning.
```

---

### Q4. Difference between Stemming and Lemmatization?

```text
Stemming:
Rule-Based

Lemmatization:
Dictionary-Based
```

---

### Q5. Why is Text Processing important?

```text
Because machine learning models require clean, structured, and meaningful text data.
```

---

# Learning Path

```text
NLP Fundamentals
      ↓
Text Cleaning
      ↓
Tokenization
      ↓
Stopword Removal
      ↓
Stemming
      ↓
Lemmatization
      ↓
Text Normalization
      ↓
Vectorization
      ↓
Word Embeddings
      ↓
Transformers
      ↓
LLMs
```

# Most Important Topics for AI Engineers

```text
Text Cleaning
Tokenization
Stopword Removal
Stemming
Lemmatization
Text Normalization
Bag of Words
TF-IDF
Word Embeddings
```

Text Processing is the foundation of all NLP systems, including:

```text
Chatbots
Search Engines
Sentiment Analysis
Machine Translation
Question Answering
RAG Systems
LLMs
Agentic AI
```

Every modern NLP pipeline begins with effective text processing before moving to embeddings, transformers, and large language models.