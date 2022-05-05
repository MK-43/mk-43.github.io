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

label이 없는 데이터

- 클러스터링(clustering)
  - 비슷해 보이는 개체들을 찾아 군집으로 묶어주는 것
  - 다양한 곳에 사용 가능
    - customer segmentation
    - data analysis: 각 클러스터별로 분석
    - 차원 축소 테크닉: 클러스터링 후 개체의 feature vector를 각 클러스터에 대한 관련성(affinity)로 변경(대게 차원이 작아짐)
    - anomaly detection: 모든 클러스터에 대한 affinity가 작은 개체는 이상값이라고 볼 수 있다. fraud detection에 사용 가능
    - semi-supervised learning: 일부만 레이블이 있는 경우, 클러스터링을 하고 레이블을 해당 클러스터에 속한 개체에 대해 설정을 해주면 그 이후에는 supervised 학습이 가능
    - image를 구분하기(image segementation)
      - 한 이미지를 여러 개의 이미지 구획으로 나누는 것
      - 이는 이미지를 분석하기 쉽게 이미지를 단순화하는 것
      - 색별로 클러스터링을 하고 그 중간색으로 해당 클러스터의 개채들의 색을 대체하는 것
- 이상치 감지(anomaly detection)
- 밀도 추정(density estimation)

## K-Means

1. 어느 정도 뭉쳐있는 그룹들의 중심을 찾고
2. 각 개체들을 해당 그룹으로 할당한다

클러스터의 개수(K)는 직접 지정해주어야 한다
군집의 blob(방울)의 지름이 크게 다르면 잘 동작하지 않는다
-> 결국 군집의 중심까지의 거리를 기준으로 군집을 할당하기 때문

### hard clustering

하나의 인스턴스에 하나의 클러스터에 할당하는 것

### soft clustering

클러스터에 할당을 하는 대신 centroid(클러스터의 중심)과의 거리를 점수화하여 표시하는 것

### K-Means Algorithm

1. centroid를 랜덤하게 K개 선택
2. 샘플에 레이블 할당
3. centroid 업데이트
4. 다시 레이블 할당

![algo](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FzfQFN%2FbtqGe8Y15aO%2FtF72kyz11YfUlsBe7Ga0L0%2Fimg.jpg)

업데이트 되는 centroids는 클러스터 내의 모든 점들에서 중심(mean)이 되는 곳
(K-Mode, K-Median)

알고리즘이 수렴하는 것은 보장이 되어 있나, 최적해가 아닌 로컬 최적해로 수렴할 수 있다
이런 위험은 centorid 초기화 방법을 향상시켜서 줄일 수 있다.

### Centroid initialization methods

- 다른 군집 알고리즘을 사용하여 centroid의 위치를 파악하여 이를 하이퍼파라미터로 넣는다  
- 또 다른 방법으로는 초기화 값을 바꿔가면서 여러 번 학습을 수행한다
  - 여러 학습 중에 가장 좋은 해를 어떻게 알 수 있을까?
    - inertia를 활용
    - 각 개체와 가장 가까운 centroid와의 Mean squared distance

> RMSE: 종속변수와 동일한 단위로 측정 됨
> MSE: 종속변수 단위의 제곱


#### K-Means++

- centroids를 서로에게 멀리 떨어지도록 선택
- 이를 통해 suboptimal로 수렴할 가능성을 줄일 수 있다

### Finding the optimal nubmer of clusters

inertia를 그대로 사용할 수 없다 -> K가 커질수록 intertia는 작아지게 되어있다.

하지만 이너셔의 감소 폭이 크게 줄어드는 지점을 선택할 수는 있다
![elbow](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcqsKHU%2FbtqGiUd9j7M%2FPJPCnGeqQm3r0QXVO4LUmk%2Fimg.jpg)

정확한 수치적인 방법: 실루엣 점수
실루엣 점수 = 모든 샘플에 대한 실루엣 계수의 평균
실루엣 계수 $\frac{(b-a)}{max(a,b)}$
a: 동일한 클러스터에 있는 다른 샘플까지의 거리(클러스터 내부의 평균거리)
b: 다음으로 가장 가까운 클러스터의 샘플들까지의 거리

-1과 1사이의 값을 갖고, +1에 가까운 경우 해당 클러스터에 잘 속해있다. -1은 잘못 할당되어있다.

![c](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FBmSwn%2FbtqGks9Buor%2FGIgN4i5ikiufyCLg335Kkk%2Fimg.jpg)

### Limits of K-Means

- K를 지정해주어야 하는데 이게 쉽지 않다
- 최적 솔루션 찾기 위해 여러번 실행해야 한다
- 클러스터들의 사이즈나 밀집도가 다르거나, 형태가 원형이 아닌 경우 성능이 떨어진다
  - 타원형의 경우 가우시안 혼합 모델은 잘 작동
- K-Means 수행 전 input의 scale을 맞춰주는 것이 중요
  - 클러스터의 형태가 길쭉해지는 것을 막을 수 있다

### Using Clustering for Image Segmentation

- semantic segmentation: 같은 오브젝트의 픽셀은 같은 segment로 할당
- color segmentation: 비슷한 색상이면 같은 segment로 할당

#### color segmentation

![img_seg](https://blog.kakaocdn.net/dn/UxqQi/btqVcrv67KQ/vHbqWszFVLpNFbgQ4sKY20/img.png)

## DBSCAN (Density-based spatial clustering of applications with noise)

핵심샘플: core points
이웃: (density-) reachable points
noise: outlier

밀집된 연속적 지역을 클러스터로 정의  

1. 알고리즘이 각 샘플에서 작은 거리 엡실론 내에 샘플이 몇개있는지 센다(e-이웃)
2. 정의한 최소 개수(min_samples)개 이상이 있다면 core instance
3. 해당 핵심 샘플에 이웃한 샘플들은 하나의 클러스터
   1. 하나의 이웃 내에 다른 핵심 샘플을 포함할 수 있음
   2. 즉 이웃의 이웃 등이 쭉 같은 클러스터로 묶임
4. 핵심 샘플도 아니고 이웃도 아닌 샘플은 이상치 

![dbscan](https://blog.kakaocdn.net/dn/cS8Kps/btqVbutsuJy/OyDgKKXKikjIrVCnrFsUhk/img.png)

- 클러스터의 모양과 개수에 상관없이 감지할 수 있다
- 이상치에 안정적, 하이퍼파라미터가 eps, min_samples 2개 뿐
- 하지만 클러스터간 밀집도가 크면 모든 클러스터를 올바르게 잡아낼 수 없다

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

모수는 2가지
- 각 정규 분포의 평균과 분산
- 각 데이터가 어떤 정규분포에 해당되는지 확률

K 값은 미리 알아야 함

#### K 선택

K-Means에서 사용하는 inertia나 실루엣 점수는 사용 불가 -> 클러스터가 타원형이거나 크기가 다를 때 안정적이지 않기 떄문

BIC나 AIC 같은 지표를 활용  
log-likelihood와 complexity에 근거한 Model selection 지표

파라미터(여기서는 클러스터)가 많은 모델에 벌칙을 가하고, 데이터에 잘 맞는(fit) 모델은 보상을 줌

값이 작을 수록 좋다

### 기댓값-최대화(Expectation-Maximization) 알고리즘 사용

#### Expectation

개별 데이터 각각에 대해 특정 정규 분포에 소속될 확률을 구하고, 가장 높은 확률을 가진 정규분포에 소속시킨다

#### Maximazation

데이터들이 특정 정규분포로 소속되면 다시 해당 정규분포의 평균과 분산을 구한다
- 해당 데이터가 발견될 수 있는 likelihood를 최대화할 수 있도록 모수를 구한다

더 이상 평균, 분산이 변경되지 않을 때, 최종 군집 결정

![EM](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fch0Rqv%2FbtqGg6M0vG3%2FodEBMumJetgsmJfYa80Z31%2Fimg.jpg)


#### Likelihood

확률: P(X|D)
확률분포가 주어졌을 때, 그 때의 관측값 X

가능도: L(D|X)
관측값이 주어졌을 때, 이것이 어떤 확률 분포에서 왔을지
PDF값
Likelihood는 움직일 수 있는 분포에 대해, 고정 된 x값 data 포인트를 넣은, y값을 나타냄.


최대우도추정
find the optimal way to fit a distribution to the data
각 관측값에 대한 총 가능도(모든 가능도의 곱)가 최대가 되게 하는 분포를 찾는 것

Maximum Likelihood Estimate for the mean, the std

MLE
