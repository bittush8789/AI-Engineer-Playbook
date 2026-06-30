# Probability for AI & Machine Learning

## What is Probability?

Probability is the branch of mathematics that measures the likelihood of an event occurring.

It answers questions like:

```text
What is the chance of rain?

What is the chance a customer files a claim?

What is the chance a transaction is fraudulent?
```

---

## Why Probability is Important in AI?

Machine Learning models make predictions based on probability.

Examples:

```text
Spam Detection
Fraud Detection
Recommendation Systems
Medical Diagnosis
LLMs
```

---

# Probability Scale

Probability ranges from:

```text
0 ≤ P(E) ≤ 1
```

Where:

```text
0 = Impossible Event

1 = Certain Event
```

---

## Examples

```text
P(Sun rises tomorrow) = 1

P(Human can fly naturally) = 0

P(Getting Head in Coin Toss) = 0.5
```

---

# Basic Terminology

## Experiment

An action that produces outcomes.

Example:

```text
Tossing a Coin
Rolling a Dice
```

---

## Outcome

Result of an experiment.

Example:

```text
Head
Tail
```

---

## Sample Space (S)

Set of all possible outcomes.

Coin Toss:

```text
S = {H, T}
```

Dice Roll:

```text
S = {1,2,3,4,5,6}
```

---

## Event

A subset of sample space.

Example:

```text
Getting Even Number
```

Event:

```text
E = {2,4,6}
```

---

# Probability Formula

## Theory

Probability =

```text
Favorable Outcomes
-------------------
Total Outcomes
```

---

## Formula

```text
P(E) = Favorable Outcomes / Total Outcomes
```

---

## Example

Rolling a dice.

Probability of getting 4:

```text
Favorable Outcomes = 1

Total Outcomes = 6
```

Result:

```text
P(4) = 1/6
```

---

# Coin Toss Example

## Probability of Head

```text
Sample Space

{H,T}
```

---

Favorable:

```text
{H}
```

---

Probability:

```text
1 / 2
```

---

Result:

```text
0.5
```

---

# Dice Example

## Probability of Even Number

Sample Space:

```text
{1,2,3,4,5,6}
```

---

Favorable Outcomes:

```text
{2,4,6}
```

---

Probability:

```text
3/6

= 1/2
```

---

# Types of Probability

## 1. Theoretical Probability

Based on mathematical calculations.

---

Example:

```text
Coin Toss
```

Probability:

```text
1/2
```

---

## 2. Experimental Probability

Based on actual observations.

---

Example:

```text
100 Coin Tosses

Head = 52

Probability = 52/100
```

---

# Complement Rule

## Theory

Probability of an event not occurring.

Formula:

```text
P(Not A)

= 1 - P(A)
```

---

## Example

Probability of rain:

```text
0.7
```

---

Probability of no rain:

```text
1 - 0.7

= 0.3
```

---

# Independent Events

## Theory

Two events that do not affect each other.

Examples:

```text
Coin Toss

Dice Roll
```

---

### Formula


::contentReference[oaicite:0]{index=0}


---

## Example

```text
Coin Head = 1/2

Dice 6 = 1/6
```

---

Result:

```text
1/2 × 1/6

= 1/12
```

---

# Conditional Probability

## Theory

Probability of an event occurring given another event has occurred.

---

### Formula


::contentReference[oaicite:1]{index=1}


---

## Example

In insurance:

```text
Probability of Claim

Given Vehicle Age > 10 Years
```

---

# Bayes Theorem

## Theory

Bayes Theorem updates probabilities based on new evidence.

---

### Formula


::contentReference[oaicite:2]{index=2}


---

## Example

Fraud Detection

```text
Prior Probability
       ↓
New Evidence
       ↓
Updated Probability
```

---

## AI Use Cases

```text
Spam Detection
Fraud Detection
Medical Diagnosis
Recommendation Systems
```

---

# Union of Events

## Theory

Probability that either event occurs.

---

### Formula


::contentReference[oaicite:3]{index=3}


---

## Example

```text
P(A)=0.5

P(B)=0.3

P(A∩B)=0.1
```

---

Result:

```text
0.5 + 0.3 - 0.1

= 0.7
```

---

# Random Variables

## Theory

A variable whose value depends on random outcomes.

---

## Example

```text
Dice Roll

X = Number Obtained
```

Possible values:

```text
1,2,3,4,5,6
```

---

# Expected Value

## Theory

Average outcome expected over many trials.

---

## Formula

```text
E(X)

= Σ xP(x)
```

---

## Example

Dice Roll

```text
E(X)

= 3.5
```

---

# Probability Distributions

## What is a Distribution?

Shows probabilities of different outcomes.

---

## Bernoulli Distribution

Outcomes:

```text
Success
Failure
```

Examples:

```text
Coin Toss
Spam Detection
```

---

## Binomial Distribution

Multiple Bernoulli Trials.

Example:

```text
10 Coin Tosses
```

---

## Normal Distribution

Most important distribution.

---

### Bell Curve

```text
         /\
        /  \
       /    \
------/------\------
```

---

Properties:

```text
Mean = Median = Mode
```

---

## AI Use Cases

```text
Data Analysis
Feature Engineering
Anomaly Detection
```

---

# Standard Score (Z-Score)

## Theory

Measures how far a value is from the mean.

---

### Formula


::contentReference[oaicite:4]{index=4}


---

## Example

Student Score:

```text
Score = 90

Mean = 70

Std Dev = 10
```

Result:

```text
z = 2
```

Meaning:

```text
2 Standard Deviations Above Mean
```

---

# Probability in Machine Learning

## Classification

Model predicts:

```text
Spam = 0.90

Not Spam = 0.10
```

---

## Fraud Detection

```text
Fraud Probability

= 0.85
```

---

## Claim Severity Prediction

```text
High Severity

= 0.92
```

---

# Probability in Deep Learning

Neural Network Output:

```text
[0.10, 0.85, 0.05]
```

Meaning:

```text
Class 2 has highest probability.
```

---

# Probability in NLP

Language Models predict next word probabilities.

Example:

```text
I love

→ AI (0.75)

→ Pizza (0.15)

→ Football (0.10)
```

---

# Probability in LLMs

When an LLM generates text:

```text
Token Probabilities
```

are calculated for every next word.

Example:

```text
The weather is

Sunny = 0.70

Rainy = 0.20

Cloudy = 0.10
```

---

# Insurance Example

## Claim Approval Probability

Features:

```text
Policy Age
Claim Amount
Claim History
```

Model Output:

```text
Approve = 0.92

Reject = 0.08
```

---

# Python Examples

## Coin Toss Probability

```python
favorable = 1
total = 2

probability = favorable / total

print(probability)
```

Output:

```text
0.5
```

---

## Dice Probability

```python
favorable = 3

total = 6

print(favorable / total)
```

Output:

```text
0.5
```

---

## Random Event

```python
import random

print(
    random.choice(
        ["Head", "Tail"]
    )
)
```

---

# Interview Questions

### Q1. What is Probability?

```text
The likelihood of an event occurring.
```

---

### Q2. What is Sample Space?

```text
The set of all possible outcomes.
```

---

### Q3. What is Conditional Probability?

```text
Probability of an event given another event has occurred.
```

---

### Q4. What is Bayes Theorem?

```text
A method for updating probabilities using new evidence.
```

---

### Q5. Why is Probability important in AI?

```text
Machine Learning models make predictions using probabilities.
```

---

# Learning Path

```text
Basic Probability
      ↓
Events
      ↓
Sample Space
      ↓
Conditional Probability
      ↓
Independent Events
      ↓
Bayes Theorem
      ↓
Random Variables
      ↓
Expected Value
      ↓
Probability Distributions
      ↓
Normal Distribution
      ↓
Machine Learning Probability
```

# Most Important Topics for AI Engineers

```text
Probability Basics
Conditional Probability
Bayes Theorem
Random Variables
Expected Value
Normal Distribution
Z-Score
Probability Distributions
```

These concepts are the mathematical foundation of:

```text
Machine Learning
Deep Learning
NLP
Transformers
LLMs
Fraud Detection
Recommendation Systems
Predictive Analytics
```