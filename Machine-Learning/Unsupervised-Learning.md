# Unsupervised Learning

## What is Unsupervised Learning?

Unsupervised Learning is a type of Machine Learning where the model learns patterns from **unlabeled data**.

Unlike Supervised Learning:

```text
Supervised Learning
=
Input + Output

Unsupervised Learning
=
Input Only
```

The model is not given the correct answers.

Its goal is to discover hidden structures, relationships, and patterns within the data.

---

# Basic Idea

```text
Raw Data
    ↓
Find Hidden Patterns
    ↓
Groups
Relationships
Anomalies
Insights
```

---

# Real-World Example

Suppose an insurance company has customer data:

| Customer ID | Age | Income |
|------------|------|---------|
| 101 | 25 | 30000 |
| 102 | 27 | 35000 |
| 103 | 55 | 120000 |
| 104 | 58 | 130000 |

No labels exist.

The algorithm automatically discovers:

```text
Young Customers

Senior Customers
```

without being told.

---

# Why Use Unsupervised Learning?

Many real-world datasets have:

```text
No Labels
```

Labeling data can be:

```text
Expensive
Time Consuming
Manual
```

Unsupervised Learning helps extract insights from such data.

---

# Types of Unsupervised Learning

```text
Clustering
Association Rule Learning
Dimensionality Reduction
Anomaly Detection
```

---

# 1. Clustering

## Theory

Clustering groups similar data points together.

---

Example:

Customer Data

```text
Customer A

Customer B

Customer C

Customer D
```

---

Output:

```text
Cluster 1

Cluster 2

Cluster 3
```

---

Visualization

```text
● ● ●

       ▲ ▲ ▲

                ■ ■ ■
```

Three clusters identified automatically.

---

# Applications of Clustering

```text
Customer Segmentation
Fraud Detection
Market Analysis
Document Grouping
Image Segmentation
```

---

# K-Means Clustering

## Most Popular Clustering Algorithm

---

Workflow:

```text
Choose K
     ↓
Assign Data Points
     ↓
Compute Centroids
     ↓
Reassign Points
     ↓
Repeat Until Stable
```

---

## Example

K = 3

Output:

```text
High Value Customers

Medium Value Customers

Low Value Customers
```

---

## Python Example

```python
from sklearn.cluster import KMeans

model = KMeans(
    n_clusters=3
)

model.fit(X)
```

---

# Hierarchical Clustering

## Theory

Builds clusters step by step.

---

Visualization

```text
A    B    C

 \  /

  Cluster

      \

      C
```

---

Result:

```text
Hierarchy Tree
```

called:

```text
Dendrogram
```

---

# DBSCAN

## Theory

Density-Based Clustering.

Groups dense regions together.

---

Advantages:

```text
Handles Noise
Finds Arbitrary Shapes
No Need for K
```

---

Applications:

```text
Fraud Detection
Geospatial Data
Network Analysis
```

---

# 2. Association Rule Learning

## Theory

Discovers relationships between items.

---

Example:

Market Basket Analysis

Customers buying:

```text
Bread
```

often buy:

```text
Butter
```

---

Rule:

```text
Bread → Butter
```

---

Applications:

```text
Recommendation Systems
Cross Selling
Retail Analytics
```

---

# Apriori Algorithm

Popular algorithm for association rules.

---

Example:

```text
Milk → Bread

Bread → Butter

Milk → Bread → Butter
```

---

# 3. Dimensionality Reduction

## Theory

Reduces the number of features while preserving information.

---

Example:

Dataset:

```text
100 Features
```

Reduced to:

```text
10 Features
```

---

Benefits:

```text
Faster Training
Less Memory Usage
Noise Reduction
Visualization
```

---

# PCA (Principal Component Analysis)

Most popular dimensionality reduction algorithm.

---

Example:

```text
100 Features
      ↓
10 Principal Components
```

---

## Python Example

```python
from sklearn.decomposition import PCA

pca = PCA(
    n_components=2
)

X_new = pca.fit_transform(X)
```

---

# Applications of PCA

```text
Computer Vision
NLP
Data Compression
Feature Reduction
```

---

# 4. Anomaly Detection

## Theory

Detects unusual observations.

---

Example:

Normal Claims:

```text
5000
7000
8000
```

---

Abnormal Claim:

```text
500000
```

---

Detected as:

```text
Anomaly
```

---

Applications:

```text
Fraud Detection
Cyber Security
Manufacturing
Healthcare
```

---

# Difference Between Supervised and Unsupervised Learning

| Feature | Supervised | Unsupervised |
|----------|-----------|-----------|
| Labels | Required | Not Required |
| Goal | Prediction | Pattern Discovery |
| Output | Known | Unknown |
| Examples | Classification, Regression | Clustering, PCA |

---

# Workflow of Unsupervised Learning

```text
Collect Data
      ↓
Data Cleaning
      ↓
Feature Engineering
      ↓
Apply Algorithm
      ↓
Find Patterns
      ↓
Analyze Results
```

---

# Insurance Example

## Customer Segmentation

Features:

```text
Age
Premium
Claim Frequency
Policy Type
```

---

Algorithm:

```text
K-Means
```

---

Output:

```text
Low Risk Customers

Medium Risk Customers

High Risk Customers
```

---

# Insurance Example 2

## Fraud Detection

Claim Amounts:

```text
5000
7000
9000
10000
500000
```

---

Model identifies:

```text
500000
```

as anomaly.

---

# Banking Example

Features:

```text
Income
Spending
Transactions
```

Output:

```text
Customer Segments
```

Used for:

```text
Marketing
Cross Selling
Offers
```

---

# E-Commerce Example

Purchase History:

```text
Laptop

Mouse

Keyboard
```

Association Rule:

```text
Laptop → Mouse
```

Used in:

```text
Recommendation Engines
```

---

# Advantages

```text
No Labels Needed
Works With Large Datasets
Finds Hidden Patterns
Useful for Exploration
```

---

# Disadvantages

```text
Harder to Evaluate
Results Can Be Ambiguous
May Produce Meaningless Clusters
```

---

# Popular Unsupervised Learning Algorithms

## Clustering

```text
K-Means
Hierarchical Clustering
DBSCAN
Gaussian Mixture Models
```

---

## Dimensionality Reduction

```text
PCA
t-SNE
UMAP
SVD
```

---

## Association Rules

```text
Apriori
FP-Growth
```

---

# Interview Questions

### Q1. What is Unsupervised Learning?

```text
A machine learning approach where models learn patterns from unlabeled data.
```

---

### Q2. What is Clustering?

```text
Grouping similar data points together.
```

---

### Q3. What is PCA?

```text
A dimensionality reduction technique that reduces features while preserving information.
```

---

### Q4. What is K-Means?

```text
A clustering algorithm that partitions data into K groups.
```

---

### Q5. Give examples of Unsupervised Learning applications.

```text
Customer Segmentation
Fraud Detection
Recommendation Systems
Anomaly Detection
```

---

# Learning Path

```text
Unsupervised Learning Basics
          ↓
Clustering
          ↓
K-Means
          ↓
Hierarchical Clustering
          ↓
DBSCAN
          ↓
Association Rules
          ↓
PCA
          ↓
Anomaly Detection
          ↓
Real-World Projects
```

# Most Important Topics for AI Engineers

```text
Clustering
K-Means
Hierarchical Clustering
DBSCAN
PCA
Dimensionality Reduction
Anomaly Detection
Association Rules
Customer Segmentation
```

Unsupervised Learning is widely used in:

```text
Fraud Detection
Customer Segmentation
Recommendation Systems
Cyber Security
Computer Vision
NLP
Insurance Analytics
Marketing Analytics
```

It is especially valuable when large amounts of data exist but labels are unavailable.