# Stemming

## What is Stemming?

Stemming is a text preprocessing technique in NLP that reduces words to their **root form (stem)** by removing prefixes and suffixes.

The goal is to treat different forms of a word as the same word.

---

# Why Stemming?

Consider these words:

```text
play
playing
played
plays
```

Although they are different words, they all represent the same concept:

```text
play
```

Stemming converts them into a common root.

---

# Example

Input:

```text
playing
played
plays
player
```

Output:

```text
play
play
play
player
```

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
Stemming
    ↓
Vectorization
    ↓
Model Training
```

---

# How Stemming Works

A stemming algorithm removes common suffixes.

---

Example

Word:

```text
playing
```

---

Remove:

```text
ing
```

---

Result:

```text
play
```

---

Another Example

Word:

```text
jumped
```

---

Remove:

```text
ed
```

---

Result:

```text
jump
```

---

# Common Transformations

| Original Word | Stem |
|--------------|------|
| playing | play |
| played | play |
| plays | play |
| jumping | jump |
| jumped | jump |
| studying | studi |
| studies | studi |

---

Notice:

```text
studi
```

is not a valid English word.

This is one limitation of stemming.

---

# Popular Stemming Algorithms

```text
Porter Stemmer
Snowball Stemmer
Lancaster Stemmer
```

---

# 1. Porter Stemmer

Most widely used stemming algorithm.

Developed by:

:contentReference[oaicite:0]{index=0}

---

Example

```text
playing → play

jumping → jump

studies → studi
```

---

# Python Example

```python
from nltk.stem import PorterStemmer

stemmer = PorterStemmer()

print(
    stemmer.stem("playing")
)
```

Output:

```text
play
```

---

# Multiple Words Example

```python
from nltk.stem import PorterStemmer

stemmer = PorterStemmer()

words = [
    "playing",
    "played",
    "plays"
]

for word in words:
    print(
        stemmer.stem(word)
    )
```

Output:

```text
play

play

play
```

---

# 2. Snowball Stemmer

Improved version of Porter Stemmer.

---

Advantages:

```text
More Accurate
Supports Multiple Languages
```

---

Example

```python
from nltk.stem import SnowballStemmer

stemmer = SnowballStemmer(
    "english"
)

print(
    stemmer.stem("running")
)
```

Output:

```text
run
```

---

# 3. Lancaster Stemmer

More aggressive stemming algorithm.

---

Example

```text
maximum
```

↓

```text
maxim
```

---

Advantages:

```text
Very Fast
```

---

Disadvantages:

```text
May Remove Too Much
```

---

# Why Use Stemming?

Benefits:

```text
Reduce Vocabulary Size
Improve Search
Faster Training
Less Memory Usage
```

---

# Example

Without Stemming

```text
play

playing

played

plays
```

Vocabulary Size:

```text
4
```

---

After Stemming

```text
play
```

Vocabulary Size:

```text
1
```

---

# Search Engine Example

User searches:

```text
play
```

Documents contain:

```text
playing

played

plays
```

---

Without Stemming:

```text
Search Misses Results
```

---

With Stemming:

```text
All Results Found
```

---

# Insurance Example

Claim Notes:

```text
Vehicle damaged during collision.

Vehicle damaging property.

Vehicle damages reported.
```

---

After Stemming:

```text
damag
```

All forms become similar.

---

Benefits:

```text
Better Claim Classification
Better Search
Reduced Vocabulary
```

---

# Stemming vs Lemmatization

| Stemming | Lemmatization |
|-----------|-----------|
| Rule-Based | Dictionary-Based |
| Faster | Slower |
| Less Accurate | More Accurate |
| May Produce Invalid Words | Produces Real Words |

---

Example

Word:

```text
studies
```

---

Stemming:

```text
studi
```

---

Lemmatization:

```text
study
```

---

Another Example

Word:

```text
better
```

---

Stemming:

```text
better
```

---

Lemmatization:

```text
good
```

---

# Limitations of Stemming

## Over-Stemming

Different words become the same stem.

---

Example

```text
university

universe
```

May become similar stems.

---

## Under-Stemming

Related words remain different.

---

Example

```text
analysis

analyze
```

May not be reduced properly.

---

# Complete Example

Sentence:

```text
Players are playing football and played yesterday.
```

---

Tokenization:

```python
[
 "Players",
 "are",
 "playing",
 "football",
 "and",
 "played",
 "yesterday"
]
```

---

Stemming:

```python
[
 "player",
 "are",
 "play",
 "footbal",
 "and",
 "play",
 "yesterday"
]
```

---

Notice:

```text
footbal
```

is not a real English word.

---

# NLTK Example

```python
from nltk.stem import PorterStemmer

stemmer = PorterStemmer()

sentence = [
    "playing",
    "played",
    "plays"
]

for word in sentence:

    print(
        stemmer.stem(word)
    )
```

Output:

```text
play

play

play
```

---

# Applications of Stemming

```text
Search Engines
Text Classification
Spam Detection
Sentiment Analysis
Document Retrieval
Chatbots
Recommendation Systems
```

---

# Interview Questions

### Q1. What is Stemming?

```text
A text preprocessing technique that reduces words to their root form by removing prefixes and suffixes.
```

---

### Q2. Why is Stemming used?

```text
To reduce vocabulary size and treat similar words as the same word.
```

---

### Q3. What is the most popular stemming algorithm?

```text
Porter Stemmer.
```

---

### Q4. Difference between Stemming and Lemmatization?

```text
Stemming is rule-based and faster.

Lemmatization is dictionary-based and more accurate.
```

---

### Q5. What is Over-Stemming?

```text
When unrelated words are reduced to the same stem.
```

---

# Learning Path

```text
Text Processing
      ↓
Tokenization
      ↓
Stopword Removal
      ↓
Stemming
      ↓
Porter Stemmer
      ↓
Snowball Stemmer
      ↓
Lemmatization
      ↓
Word Embeddings
      ↓
Transformers
```

# Most Important Topics for AI Engineers

```text
Porter Stemmer
Snowball Stemmer
Root Words
Vocabulary Reduction
Over-Stemming
Under-Stemming
Text Normalization
```

Stemming is a foundational NLP preprocessing technique used in:

```text
Search Engines
Document Retrieval
Text Classification
Sentiment Analysis
Spam Detection
Information Retrieval Systems
```

Although modern Transformer models often rely less on stemming because of advanced tokenization techniques, understanding stemming remains important for classical NLP and machine learning pipelines.