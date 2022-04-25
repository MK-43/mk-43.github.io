---
title:  "[ml] ch.1 The Fundamentals of Machine Learning"
excerpt: ""

categories:
  - ml
tags:
  - [hands-on]

toc: true
toc_sticky: true
 
date: 2022-04-21
last_modified_at: 2022-04-21
---
### The main steps

### Supervised/Unsupervised learning

#### Supervised learning

- **classification**

- **Regression**: given a set of *features* called *predictors*, predict a *target* numeric value  
  - **logistic regression**: commonly used for classification
- K-Nearest Neighbors  
- Linear Regression  
- Support Vector Machines(SVMs)  
- Decision tress and random forests  
- Neural networks

#### Unsupervised learning

- Clustering  
  - K-Means
  - DBSCAN
  - Hierarchical Cluster Analysis (HCA)
- Anomaly detection and novelty detection
  - One-class SVM
  - Isolation Forest
- Visualization and dimensionality reduction
  - Principal Component Analysis (PCA)
  - Kernel PCA
  - Locally Linear Embedding (LLE)
  - t-Distributed Stochastic Neighbor Embedding (t-SNE)
- Association rule learning
  - Apriori
  - Eclat

  > Visualization algorithms try to preserve as much structure as they can (e.g., trying to keep separate clusters in the input space from overlapping in the visualization)

**dimensionality reduction**: to simplify the data without losing too much information
- merge several correlated features into one
- feature extraction


### Semisupervised learning

### Reinforcement learning

### Batch and online learning

#### Batch learning

it must be trained using **all the available data**  
1. the system is learned
2. it is launched into production and runs without learning anymore
called *offline learning*

#### online learning

you train the system incrementally by feeding it data instances sequentially, either individually or in small groups called *mini-batches*

- great for systems that receive data as a continuous flow (e.g., stock prices) and need to adapt to change rapidly or autonomously
- can be used to train systems on huge datasets that cannot fit in one machines' main memory (called *out-of-core learning*)

*learning rate*: how fast a learning system should adapt to chaning data