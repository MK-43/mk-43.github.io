---
title:  "[hands-on] CNN"
excerpt: ""

categories:
  - ml
tags:
  - [hands-on]

toc: true
toc_sticky: true
use_math: true
 
date: 2022-05-01
last_modified_at: 2022-05-01
---

taking a filter, sliding it spatially over the image, computing the dot product at every location.

## The Architecture of the Visual Cortex

*local receptive field*라는 제한 크기의 시각체를 통해서 사물을 인지한다.  
몇몇 뉴런들은 수평선, 수직선 등 특정한 이미지에만 반응한다.  
![Fig14-1](https://velog.velcdn.com/images/mk-43/post/7fbf0af2-7ae0-4781-a6aa-d6e95674cae7/image.png)

MLP는 보통 fully connected networks이다.

> fully connected networks: 한 레이어의 모든 뉴론이 다음 레이어의 모든 뉴론에 fully 연결되어 있다

fully connected networks는 오버피팅하는 경향이 있는데, 이를 regularization해줘야 한다.  

> 그냥 MLP 사용하면 안되나?  
> 1. data의 형상이 무시 됨(가령, 세로, 가로, 채널로 구성 된 3차원 데이터를 MLP로 넣으면 단순 1차원으로 평탄화하여 학습)  
> 2. 인풋 데이터가 커지면 학습이 어려움  
> eg. 100x100 이미지의 경우, 인풋이 10,000px인데 첫번째 레이어가 1,000뉴런을 가지면 connections이 천만개

### Convolution

Mathematical operation on two functions that produces a third function (f*g) that expresses how the shape of one is modified by the other.

새로운 함수를 만들어 내는 두 함수에 대한 연산.  
한 함수 형태가 다른 함수에 의해 어떻게 영향 받는지를 나타냄.

defined as the integral of the product of the two functions after one is reversed and shifted.

#### Convolutional Layer

오직 filter안에 있는 뉴런이랑만 연결되어 있다(not fully connected)

#### zero padding

이전 레이어와의 크기를 유지하기 위해 가장자리에 0으로 채움

#### Stride

The shift from one receptive field to the next
윈도우 사이 이동하는 거리

### Filter (Convolution Kernel)

The vector of **weights** and the **bias**.  
*receptive field*는 인지하는 윈도우를 말하고, 실제 그 가중치과 편향을 가진 벡터를 filter라고 한다.  
특정 feature를 나타낸다.  
CNN 특징 중 하나가 여러 뉴런들이 하나의 필터를 공유할 수 있다는 것인데, 이로 memory footprint를 줄일 수 있다.

> memory footprint: 프로그램이 동작할 때 사용하는 메모리의 양

$$
\begin{bmatrix}
0 & 0 & 0 & 1 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 & 0 & 0
\end{bmatrix}
$$

#### Feature Map

합성곱 계층의 입출력 데이터를 특징 맵이라고 한다.  
Convolutional layer가 학습하면서 task에 맞는 가장 유용한 필터를 찾을 것

하나의 특징 맵에 있는 뉴런들은 모두 같은 파라미터(같은 가중치와 편향)를 공유한다.  
➜ 이는 모델의 파라미터의 갯수를 줄이는데 기여한다  
❓ ➜ CNN은 어느 한 위치에서 특정 패턴을 인지하면 다른 위치에 있는 해당 패턴도 인지할 수 있다.


