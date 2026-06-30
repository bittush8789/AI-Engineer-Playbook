# Lemmatization

## What is Lemmatization?

Lemmatization is a text preprocessing technique that converts words into their **base dictionary form**, called a **lemma**.

Unlike stemming, lemmatization uses:

```text
Vocabulary
Grammar Rules
Part-of-Speech (POS)
```

to find meaningful root words.

---

# Why Lemmatization?

Consider:

```text
running
runs
ran
```

All represent:

```text
run
```

Lemmatization converts them into the correct dictionary word.

---

# Example

Input:

```text
running
ran
runs
```

Output:

```text
run
run
run
```

---

# Stemming vs Lemmatization

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

# Advantages

```text
Produces Real Words
More Accurate
Preserves Meaning
```

---

# Python Example

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

# Example Sentence

Input:

```text
The boys are playing football.
```

---

After Lemmatization:

```text
boy
play
football
```

---

# Applications

```text
Search Engines
Text Classification
Sentiment Analysis
Chatbots
Information Retrieval
```

---

# Word Embeddings

## What are Word Embeddings?

Word Embeddings are numerical vector representations of words that capture their meaning and relationships.

---

# Why Word Embeddings?

Machines cannot understand:

```text
dog
cat
car
```

directly.

Need conversion:

```text
Text
 ↓
Numbers
```

---

# Traditional Encoding Problem

## One-Hot Encoding

```text
Dog = [1,0,0]

Cat = [0,1,0]

Car = [0,0,1]
```

---

Problem:

```text
No Meaning Captured
```

Dog and Cat appear completely unrelated.

---

# Word Embeddings Solution

Represent words as dense vectors.

Example:

```text
Dog

↓

[0.23, 0.81, 0.15]
```

---

```text
Cat

↓

[0.25, 0.79, 0.18]
```

---

Notice:

```text
Dog and Cat
```

have similar vectors.

---

# Semantic Meaning

Embeddings learn relationships.

Example:

```text
King - Man + Woman
```

≈

```text
Queen
```

---

This is possible because embeddings capture semantic meaning.

---

# Visualization

```text
Animal Space

Dog ●

Cat ●

Tiger ●

Car ▲
```

Animals are close together.

---

# Benefits of Word Embeddings

```text
Capture Meaning
Capture Similarity
Dense Representation
Better Model Performance
```

---

# Types of Word Embeddings

```text
Word2Vec
GloVe
FastText
BERT Embeddings
Sentence Embeddings
```

---

# Word2Vec

## What is Word2Vec?

Word2Vec is one of the most influential word embedding algorithms.

Developed by:

:contentReference[oaicite:0]{index=0}

in 2013.

---

# Goal

Learn vector representations of words from large text corpora.

---

# Basic Idea

Words appearing in similar contexts have similar meanings.

---

Example

Sentence:

```text
The cat sits on the mat.
```

---

Word:

```text
cat
```

Context:

```text
The
sits
on
```

---

Word2Vec learns:

```text
cat
```

is related to:

```text
dog
pet
animal
```

---

# Word2Vec Architecture

Two main approaches:

```text
CBOW
Skip-Gram
```

---

# 1. CBOW (Continuous Bag of Words)

## Theory

Predicts a word using surrounding context.

---

Example

Sentence:

```text
I love Machine Learning
```

Input:

```text
I
love
Learning
```

Predict:

```text
Machine
```

---

Visualization

```text
Context Words
      ↓
Predict Target Word
```

---

# Advantages

```text
Fast Training
Works Well On Large Data
```

---

# 2. Skip-Gram

## Theory

Predicts surrounding words from a target word.

---

Example

Input:

```text
Machine
```

Predict:

```text
I
love
Learning
```

---

Visualization

```text
Target Word
      ↓
Predict Context Words
```

---

# Advantages

```text
Better For Rare Words
Higher Accuracy
```

---

# CBOW vs Skip-Gram

| CBOW | Skip-Gram |
|--------|--------|
| Context → Word | Word → Context |
| Faster | Slower |
| Common Words | Rare Words |
| Less Accurate | More Accurate |

---

# Word2Vec Training Process

```text
Large Text Corpus
      ↓
Generate Context Windows
      ↓
Train Neural Network
      ↓
Learn Word Vectors
```

---

# Example Embeddings

```text
King

↓

[0.25, 0.84, 0.12]
```

---

```text
Queen

↓

[0.27, 0.82, 0.14]
```

---

Vectors become close because meanings are related.

---

# Similarity Measurement

Most commonly:

```text
Cosine Similarity
```

---

Formula:

```text
Similarity

=

cos(θ)
```

---

Range:

```text
1 → Similar

0 → Unrelated

-1 → Opposite
```

---

# Python Example

```python
from gensim.models import Word2Vec

sentences = [

    ["i","love","nlp"],

    ["nlp","is","awesome"]
]

model = Word2Vec(

    sentences,

    vector_size=100,

    window=5,

    min_count=1
)
```

---

# Finding Similar Words

```python
model.wv.most_similar(
    "nlp"
)
```

---

Output:

```text
machine_learning

ai

deep_learning
```

---

# Applications of Word2Vec

```text
Search Engines
Recommendation Systems
Chatbots
Sentiment Analysis
Question Answering
Document Similarity
```

---

# Insurance Example

Claim Notes:

```text
Vehicle collision damage
```

---

Word2Vec learns:

```text
collision
```

is similar to:

```text
accident

crash

impact
```

---

Useful for:

```text
Claim Classification
Fraud Detection
Document Search
```

---

# Limitations of Word2Vec

## Static Embeddings

Same word always gets same vector.

---

Example

Word:

```text
bank
```

Meaning 1:

```text
River Bank
```

Meaning 2:

```text
Financial Bank
```

---

Word2Vec:

```text
Same Embedding
```

---

Problem:

```text
Cannot Understand Context
```

---

# Modern Alternatives

```text
FastText
GloVe
ELMo
BERT
Sentence Transformers
```

---

# Interview Questions

### Q1. What is Lemmatization?

```text
A text preprocessing technique that converts words into their dictionary root form.
```

---

### Q2. Difference between Stemming and Lemmatization?

```text
Stemming:
Rule-Based

Lemmatization:
Dictionary & Grammar Based
```

---

### Q3. What are Word Embeddings?

```text
Dense vector representations that capture semantic meaning of words.
```

---

### Q4. What is Word2Vec?

```text
A neural network-based algorithm used to learn word embeddings from text data.
```

---

### Q5. Difference between CBOW and Skip-Gram?

```text
CBOW:
Predicts target word from context.

Skip-Gram:
Predicts context from target word.
```

---

# Learning Path

```text
Text Processing
      ↓
Tokenization
      ↓
Stemming
      ↓
Lemmatization
      ↓
Word Embeddings
      ↓
Word2Vec
      ↓
GloVe
      ↓
FastText
      ↓
Contextual Embeddings
      ↓
Transformers
      ↓
LLMs
```

# Most Important Topics for AI Engineers

```text
Lemmatization
Word Embeddings
Dense Vectors
Semantic Similarity
Word2Vec
CBOW
Skip-Gram
Cosine Similarity
Context Windows
Embedding Spaces
```

These concepts form the foundation of modern NLP systems and lead directly into:

```text
GloVe
FastText
Transformers
BERT
Sentence Embeddings
RAG Systems
Large Language Models (LLMs)
```

Before modern Transformer architectures, Word2Vec revolutionized NLP by enabling machines to understand semantic relationships between words rather than treating them as simple tokens.