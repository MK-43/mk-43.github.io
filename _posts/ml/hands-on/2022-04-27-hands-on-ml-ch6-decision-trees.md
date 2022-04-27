---
title:  "[ml] ch.6 decision trees"
excerpt: ""

categories:
  - ml
tags:
  - [hands-on]

toc: true
toc_sticky: true
use_math: true

date: 2022-04-27
last_modified_at: 2022-04-27
---

![iris](https://miro.medium.com/max/1210/1*wFt86uy-rLMTF67iG7zo1w.png)

### Estimating Class Probabilities

Probability that an instance belongs to a particular class K using *value*

## The CART Training Algorithm

*Classification and Regression Tree*

searches for the pair $(k, t_{k})$ that produces the purest subsets

keeps spliting the subsets until it
1. reaches the maximum depth  
2. cannot find a split that will reduce impurity

## Computational Complexity

## Gini Impurity or Entropy?

*entropy* is zero when it contains instances of only one class

➜ No big diff

## Regularization

*ruglarization*: need to restrict the Decision Tree's freedom during training to prevent overfitting

➜ max_depth

## Regression

