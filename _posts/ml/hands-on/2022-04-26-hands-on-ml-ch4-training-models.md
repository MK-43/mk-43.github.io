---
title:  "[ml] ch.4 Training Models"
excerpt: ""

categories:
  - ml
tags:
  - [hands-on]

toc: true
toc_sticky: true
# use_math: true
 
date: 2022-04-26
last_modified_at: 2022-04-26
---

- using a direct "closed-form" equation
- using an iterative optimization approach called Gradient Descent (GD) that gradually tweaks the model parameters to minimize the cost function over the training set, eventually converging to the same set of parameters as the GD.

### Linear Regression

Assumption: the data is linear

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

Use grid serach

#### 

1. set a very large number of iterations  
2. interrupt the algorithm when the gradient vector becomes tiny  

<!-- TODO: Fix inline  -->
$|norm|<\epsilon$ 
➜ stop!

### Stochastic Gradient Descent

picks a random instance(can vary) in the training set at every step and computes the gradients based only on that single instance.  
➜ the training instances must be independent and identically distributed (IID)

the cost function will bounce up and down, decreasing only on average.

epoch

### Mini-batch Gradient Descent

computes the gradients on small random sets of instances called *mini-batch*  

Batch GD stops at the minimum,  
But both stochastic GD and Mini-batch GD continue to walk around

|GD|training set|at the minimum|
|---|---|---|
|Batch GD| full training set| stops at the minimum|
|Stochastic GD| just one instance | keeps walking around|
| Mini-batch GD| small random sets of instances|keeps walking around|

➜ gradually reduce the learning rate during training to avoid GD from bouncing around the optimum at the end

### Polynomial Regression

For non-linear model, add powers of each feature as new features

> ❓ Polynomial Regression is capable of finding relationships between features

### Learning Curve

plots of the model's performance on the training set and the validation set as a function of the training set size ➜ $f(\text{training set size})$

#### Over-Fitting, Under-Fitting

| |training data| validation data|
|---|---|---|
|overfitting|performs well|generalizes poorly|
|underfitting|poorly|poorly|

**underfitting**
![underfitting](https://velog.velcdn.com/images/mk-43/post/ea798f51-ea47-48ab-9440-523195dcdce9/image.png)

**overfitting**  
![overfitting](https://velog.velcdn.com/images/mk-43/post/5143b296-c028-443f-824b-a73856d6c5be/image.png)

Refer to [Over-Fitting/Under-Fitting](../quest-for-ml/2022-04-26-quest-ch-2.md#over-fitting-under-fitting)

> ❓ bias, variance, irreducible error

Bias  
This part of the generalization error is due to wrong assumptions,
such as assuming that the data is linear when it is actually quadratic.
A high-bias model is most likely to underfit the training data.

Variance  
This part is due to the model’s excessive sensitivity to small
variations in the training data. A model with many degrees of
freedom (such as a high-degree polynomial model) is likely to have
high variance and thus overfit the training data.

Irreducible error  
This part is due to the noisiness of the data itself. The only way to
reduce this part of the error is to clean up the data (e.g., fix the data
sources, such as broken sensors, or detect and remove outliers).
Increasing a model’s complexity will typically increase its variance and
reduce its bias. Conversely, reducing a model’s complexity increases its
bias and reduces its variance. This is why it is called a trade-off.

### Regularized Linear Models

regularize(constrain) the model (규제 선형 회귀)
degree of freedom &darr; ➜ overfitting &darr;  
reduce the number of polynomial degress

> training에 쓰이는 cost function과 testing에 쓰이는 함수가 보통 다르다
> 1. for regularization  
> 2. 최종 testing의 경우, 최종 목적에 따라 다르게 지표를 설정하기 때문.  
> 가령, log loss함수로 학습하고, 최종에서는 precision/reacall을 사용

cost함수 = 학습데이터 잔차 오류 최소화 + 회귀계수 크기 제어

alpha값을 크게 하면 weight을 줄여서라도 전체 값을 낮추려고 한다 ➜ 변수 줄임

#### Ridge Regression

use $l_{2}$ norm 

#### Rasso

use $l_{1}$ norm

#### Elastic Net

a middle ground between Ridge and Lasso

#### Early Stopping

stop training as soon as the validation error reaches a minimum

### Logistic Regression

used to estimate the probability that an instance belongs to a particular class ➜ binary classifier  

$$
\begin{equation}
    \hat{y} = \begin{cases}
        0 & \text{if}\ \hat{p} < 0.5 \\
        1 & \text{if}\ \hat{p} \ge 0.5 \\
    \end{cases}
\end{equation}
$$

$$
  \hat{p} = h_{\theta}(x) = \sigma(x^{T}\theta)
$$

$$
  \sigma(t) = \frac{1}{1+\text{exp}(-t)}
$$

the score *t* is often called the *logit*.  
logit function $logit(p) = log(p/(1-P))$ is the inverse of the logistic function.  

![logistic-function](https://upload.wikimedia.org/wikipedia/commons/thumb/8/88/Logistic-curve.svg/640px-Logistic-curve.svg.png?1651011186528)

#### Training and Cost Function

to set the parameter vector $\theta$ so that the model estimates high probabilities for positive instances ($y=1$) and low probabilities for negative instances($y=0$)

[//]: <TODO: fix it>
$$
\begin{equation}
  c(\theta) = \begin{cases}
                -log(\hat{p}), & \text{if}\ y=1 \\
                -log(1-\hat{p}), & \text{if}\ y=0 \\
              \end{cases}
\end{equation}
$$

Logistic Regression cost function (*log loss*)  
Cost function is convex ➜ guaranteed to find the global minimum

#### Decision boundary

y=0과 y=1을 가르는 경계선  
![decision_boundary](https://wikidocs.net/images/page/4288/logreg303.PNG)

decision boundary는 $\theta$에 의해 결정 됨.

### Softmax Regression (Multinomial Logistic Regression)

The logistic regression model that is generalized to support multiple classes directly ➜ 다중 클래스 분류

가령, 각 클래스에 시그모이드 함수를 적용하면 p(A)=0.8, p(B)=0.2, p(C)=0.4라고 했을 때  
이것들을 총 합이 1인 예측값을 얻도록 바꾸는 것

1. computes a score $s_{k}(x)$ for each class k,
2. estimates the probability of each class by applying the softmax function  

**score** $s_{k}(x) = x^{T}\theta^{(k)}$

$$
\hat{p}_{k} = \sigma(s(x))_k = \frac{\text{exp}(s_{k}(x))}{\sum_{j=1}^{k}\text{exp}(s_{j}(x))}
$$

> 분류하고자 하는 클래스가 K개 있을 때, K차원의 벡터를 입력 받아 모든 벡터의 원소의 값을 [0, 1] 값으로 변경하여 다시 K차원의 벡터를 반환한다.  
> ![softmax_img](https://vitalflux.com/wp-content/uploads/2020/10/Softmax-Function-1024x520.png)

> $$
> P(y=j \mid{x}) = \frac{e^{x^{T}w_{j}}}{\sum^{K}_{k=1}e^{x^{T}wk}}
> $$
>![softmax](https://production-media.paperswithcode.com/methods/Screen_Shot_2020-05-23_at_11.56.35_PM_yh1VO82.png)

#### Cross entropy

cost function

$$
    \text{cost} = -\frac{1}{m}\sum_{i=1}^{m}\sum_{k=1}^{K}y_{k}^{(i)}\text{log}(\hat{p}_k^{(i)})
$$

When K=2, equivalent to the Logistic Regression's cost function (log loss)