---
title:  "[hands-on] unsupervised learning"
excerpt: ""

categories:
  - ml
tags:
  - [hands-on]

toc: true
toc_sticky: true
use_math: true
 
date: 2022-05-03
last_modified_at: 2022-05-03
---

inertia

각 개체에서부터 가장 가까운 중심점까지의 mean squared distance

#### MSE vs RMSE

RMSE: 종속변수와 동일한 단위로 측정 됨
MSE: 종속변수 단위의 제곱


## Gaussian Mixtures

### Univariate

$$
N(x|\mu ,{\sigma}^2 )=\frac { 1 }{ \sqrt { 2\pi  } \sigma  } \exp\left( -\frac { { (x-\mu ) }^{ 2 } }{ 2{ \sigma  }^{ 2 } }  \right)
$$
![nor_dist](https://i.imgur.com/28YetdP.png)

### Multivariate Normal Distribution
$$
N({\bf x}|{\pmb \mu}, {\bf \Sigma}) = \dfrac{1}{(2\pi)^{D/2}|{\bf \Sigma}|^{1/2}}\exp\left\{-\frac{1}{2}({\bf x}-{\pmb \mu})^T{\bf \Sigma}^{-1}({\bf x}-{\pmb \mu})\right\}
$$

![multivar_dist](https://i.imgur.com/V7DNP2Z.png)

> covariance matrix
> 각 요소의 쌍에 대해 공분산은 주는 정사각 함수
$$
    cov[X_{i}, X_{j}]
$$
> 공분산: joint variability of two random variables
> 공분산의 부호는 두 변수의 선형 관계를 보여준다
$$
cov(X,Y) = E[(X-E[X])(Y-E[Y])]
$$


### Gaussian Mixture Model

K개의 정규분포의 가중합으로 데이터를 표현하는 확률 모델
$$
f\left( \mathbf{x} | \mathbf{\lambda}  \right) = \sum_{ j=1  }^{ K }{ c_j N({\bf x}|{\pmb \mu_j}, {\bf \Sigma}_j) } \\ \mathbf{\lambda} =\left\{ { c }_{ j }, \mathbf{ \mu  }_{ j },\mathbf{ \Sigma  }_{ j } \right\} \text{,   }j=1,.., K
$$

![gau_mix_model](https://i.imgur.com/u7tDOSE.png)

K 값은 미리 알아야 함