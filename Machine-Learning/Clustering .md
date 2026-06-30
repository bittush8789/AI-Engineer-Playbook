# Clustering in Machine Learning

## What is Clustering?

Clustering is an **Unsupervised Learning** technique that groups similar data points together.

Unlike Supervised Learning:

```text
Supervised Learning
=
Input + Labels

Clustering
=
Input Only
```

No target variable exists.

The algorithm automatically discovers hidden groups in data.

---

# Why Clustering?

Businesses often have large amounts of unlabeled data.

Examples:

```text
Customer Data
Claims Data
Transaction Data
Website Users
Products
```

Clustering helps identify:

```text
Patterns
Groups
Segments
Relationships
```

---

# Basic Idea

Suppose we have customers:

```text
Customer A

Customer B

Customer C

Customer D
```

---

The algorithm groups similar customers.

Output:

```text
Cluster 1

Cluster 2

Cluster 3
```

---

# Visualization

Before Clustering:

```text
●      ▲

      ●

▲             ■

        ■
```

---

After Clustering:

```text
● ● ●

      ▲ ▲ ▲

              ■ ■ ■
```

---

# Real-World Example

## Customer Segmentation

Features:

```text
Age
Income
Spending Score
```

---

Output:

```text
High Value Customers

Medium Value Customers

Low Value Customers
```

---

# Clustering Workflow

```text
Collect Data
      ↓
Data Cleaning
      ↓
Feature Scaling
      ↓
Apply Clustering Algorithm
      ↓
Discover Groups
      ↓
Business Insights
```

---

# Types of Clustering Algorithms

```text
K-Means Clustering
Hierarchical Clustering
DBSCAN
Gaussian Mixture Models
```

---

# 1. K-Means Clustering

## What is K-Means?

K-Means is the most popular clustering algorithm.

---

Goal:

```text
Divide Data Into K Groups
```

---

Example:

```text
K = 3
```

Output:

```text
Cluster 1

Cluster 2

Cluster 3
```

---

# How K-Means Works

## Step 1

Choose number of clusters.

```text
K = 3
```

---

## Step 2

Initialize cluster centers.

```text
Centroids
```

---

## Step 3

Assign each point to nearest centroid.

---

## Step 4

Recalculate centroids.

---

## Step 5

Repeat until stable.

---

# K-Means Workflow

```text
Choose K
     ↓
Initialize Centroids
     ↓
Assign Points
     ↓
Update Centroids
     ↓
Repeat
```

---

# Example Dataset

| Customer | Income |
|------------|---------|
| A | 30000 |
| B | 35000 |
| C | 120000 |
| D | 130000 |

---

Output:

```text
Cluster 1

Low Income Customers
```

```text
Cluster 2

High Income Customers
```

---

# Python Example

```python
from sklearn.cluster import KMeans

model = KMeans(
    n_clusters=2
)

model.fit(X)

clusters = model.labels_

print(clusters)
```

---

# Choosing K

## Elbow Method

Most common approach.

---

Example:

```text
K = 1

K = 2

K = 3

K = 4

K = 5
```

---

Plot:

```text
Error
 ^
 |
 |\
 | \
 |  \
 |   \__
 +------------>
        K
```

---

The bend:

```text
Elbow Point
```

represents optimal K.

---

# Advantages of K-Means

```text
Fast
Simple
Scalable
Easy to Understand
```

---

# Disadvantages

```text
Need K in Advance
Sensitive to Outliers
Works Best on Circular Clusters
```

---

# 2. Hierarchical Clustering

## Theory

Builds clusters gradually.

---

Starts with:

```text
Each Point = Individual Cluster
```

---

Then merges closest clusters.

---

# Visualization

```text
A

B

C

D
```

---

Merge:

```text
A + B

C + D
```

---

Then:

```text
(A+B) + (C+D)
```

---

# Dendrogram

Hierarchical clustering creates:

```text
Tree Structure
```

called:

```text
Dendrogram
```

---

Example:

```text
      -----
     |     |
   ---    ---
  A  B   C  D
```

---

# Advantages

```text
No Need for K Initially
Good Visualization
```

---

# Disadvantages

```text
Slow on Large Data
```

---

# 3. DBSCAN

## What is DBSCAN?

Density-Based Spatial Clustering of Applications with Noise.

---

Groups dense regions together.

---

Visualization

```text
● ● ● ●

● ● ●

            ▲

▲ ▲ ▲ ▲

▲ ▲
```

---

# Benefits

```text
Handles Noise
Finds Arbitrary Shapes
No Need to Specify K
```

---

# Applications

```text
Fraud Detection
GPS Data
Network Analysis
Cyber Security
```

---

# Example

Claim Amounts:

```text
5000
7000
8000
9000
1000000
```

---

Output:

```text
1000000
```

identified as:

```text
Noise
```

---

# 4. Gaussian Mixture Models (GMM)

## Theory

Assumes data comes from multiple Gaussian distributions.

---

Unlike K-Means:

```text
Soft Clustering
```

---

Example:

Customer belongs:

```text
70% Cluster A

30% Cluster B
```

---

Instead of:

```text
100% Cluster A
```

---

# Clustering Evaluation

Since labels are unavailable:

```text
Traditional Accuracy Cannot Be Used
```

---

# Silhouette Score

Most common clustering metric.

---

Range:

```text
-1 to 1
```

---

Interpretation:

```text
1 = Excellent Clusters

0 = Overlapping Clusters

-1 = Poor Clusters
```

---

# Inertia

Used in K-Means.

Measures:

```text
Distance Between Points And Centroids
```

---

Lower:

```text
Better
```

---

# Clustering vs Classification

| Clustering | Classification |
|------------|------------|
| Unsupervised | Supervised |
| No Labels | Labels Required |
| Discover Groups | Predict Classes |
| Unknown Output | Known Output |

---

# Insurance Example

## Customer Segmentation

Features:

```text
Premium Amount
Claim Frequency
Policy Type
```

---

Output:

```text
Low Risk Customers

Medium Risk Customers

High Risk Customers
```

---

Business Benefits:

```text
Personalized Pricing

Targeted Marketing

Better Retention
```

---

# Insurance Example 2

## Fraud Detection

Claim Data:

```text
5000
7000
8000
9000
500000
```

---

Cluster Analysis:

```text
Normal Claims

Suspicious Claims
```

---

# Banking Example

Features:

```text
Income
Transactions
Credit Score
```

---

Output:

```text
Premium Customers

Regular Customers

Risk Customers
```

---

# E-Commerce Example

Features:

```text
Purchase Frequency
Order Value
Visits
```

---

Output:

```text
VIP Customers

Occasional Buyers

Inactive Users
```

---

# Complete Scikit-Learn Example

```python
from sklearn.cluster import KMeans

model = KMeans(
    n_clusters=3
)

model.fit(X)

clusters = model.predict(X)

print(clusters)
```

---

# Interview Questions

### Q1. What is Clustering?

```text
An unsupervised learning technique that groups similar data points together.
```

---

### Q2. What is K-Means?

```text
A clustering algorithm that partitions data into K clusters.
```

---

### Q3. What is the Elbow Method?

```text
A technique used to determine the optimal number of clusters.
```

---

### Q4. What is DBSCAN?

```text
A density-based clustering algorithm that can detect noise and arbitrary-shaped clusters.
```

---

### Q5. Difference between Clustering and Classification?

```text
Clustering:
No Labels

Classification:
Labels Required
```

---

# Learning Path

```text
Clustering Basics
        ↓
K-Means
        ↓
Elbow Method
        ↓
Hierarchical Clustering
        ↓
DBSCAN
        ↓
Gaussian Mixture Models
        ↓
Silhouette Score
        ↓
Real-World Projects
```

# Most Important Topics for AI Engineers

```text
K-Means
Centroids
Elbow Method
Hierarchical Clustering
DBSCAN
GMM
Silhouette Score
Customer Segmentation
Anomaly Detection
```

Clustering is widely used in:

```text
Insurance Analytics
Fraud Detection
Customer Segmentation
Recommendation Systems
Marketing Analytics
Cyber Security
Healthcare Analytics
Retail Analytics
```

It is one of the most valuable techniques when working with large volumes of unlabeled data.