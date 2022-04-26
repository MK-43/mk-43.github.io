---
title:  "[ml] ch.4 Training Models"
excerpt: ""

categories:
  - ml
tags:
  - [hands-on]

toc: true
toc_sticky: true
 
date: 2022-04-26
last_modified_at: 2022-04-26
---

- using a direct "closed-form" equation
- using an iterative optimization approach called Gradient Descent (GD) that gradually tweaks the model parameters to minimize the cost function over the training set, eventually converging to the same set of parameters as the GD.

### Linear Regression

In practice, RMSE 대신 MSE 사용

#### The normal equation

closed-form solution: 
Normal equation may not work if $X^\intercal X$ is not invertible, such as if $m < n$ or if some features are redundantm but pseudoinverse is always defined

*pseudoinverse* is computed using a standard matrix factorization technique called *Singular Value Decomposition* (SVD)

#### computational complexity

$(n+1)\times (n+1)$ &rarr; $O(n^{2.4})$ to $O(n^{3})$

depending on the implementation

### Gradient Descent

tweak parameters iteratively in order to minimize a cost function  
used when a large number of features or too many training instances to fit in memory

MSE cost function of **Linear Regression** is a **convex function**
> convex function: the straight line between any pair of points on the curve to be above  
> 그래프의 어느 두 점을 이어 직선을 만들어도 그 직선은 그래프 위에 있다.  

if the features have very **different scales**, it will take a long time to reach the minimum.  
Thus, do [**feature normalization**](../quest-for-ml/2022-04-26-quest-ch-1.md#feature-normalization)

처음 시작점을 설정하는게 중요한데, 그냥 random initialization

also the size of the steps, determined by *learning rate* is an important parameter.  
too small &rarr; takes a long time  
too high &rarr; jump across the valley and diverge  

training a model &rarr; searching for a combination of model parameters that minimize a cost function.

### Batch Gradient Descent

*partial derivative*: how much the cost function will change if you change $\theta_{j}$ just a little bit

it uses the whole batch of training data at every step.  
GD is faster than Normal equation or SVD decomposition.

$$
    \theta^{(\text{next step})} = \theta - \eta\nabla_{\theta}MSE(\theta)
$$

#### how to find a good learning rate?

grid serach

1. set a very large number of iterations  
2. interrupt the algorithm when the gradient vector becomes tiny  

$|norm|<\epsilon$ &rarr; stop!

### Stochastic Gradient Descent

picks a random instance(can vary) in the training set at every step and computes the gradients based only on that single instance.  
➜ the training instances must be independent and identically distributed (IID)

the cost function will bounce up and down, decreasing only on average.

epoch