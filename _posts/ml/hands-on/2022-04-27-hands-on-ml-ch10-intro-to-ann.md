---
title: "[ml] ch.10 Introduction to Artificial Neural Networks with Keras"
excerpt: ""

categories:
  - ml
tags:
  - [hands-on]

toc: true
toc_sticky: true
use_math: true

date: 2022-04-26
last_modified_at: 2022-05-12
---

## From Biological to Artificial Neurons

### The Perceptron

- 단순한 ANN 구조 중 하나
- TLU에 기반함
- 인풋과 아웃풋은 숫자 값이다.
- 각각의 인풋값은 weight과 연관된다.

#### Threshold Logic Unit (TLU)

- 인공 뉴런

![TLU](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdzHbTo%2Fbtq53upblrI%2FsZQKjqrh4TlJX4uXjgf0xk%2Fimg.png)  

1. 각 인풋의 가중평균을 구한다.
2. step function에 넣는다. (heaviside step, sign 함수가 사용됨)
3. 출력값을 낸다.

$$  
\begin{equation}  
    \text{heaviside(z)} = \begin{cases}  
        0 & \text{if}\ z < 0 \\  
        1 & \text{if}\ z \ge 0 \\  
    \end{cases}  
\end{equation}  
$$  

➜ TLU를 학습시키는 것은 가중치(w)를 찾는 것  

_fully connected layer(dense layer)_: 해당 층의 모든 뉴런이 이전 층의 모든 뉴런과 연결되는 경우  

#### Multilayer Percentron (MLP)

다수의 퍼셉트론은 쌓아 올려서 만든다  
