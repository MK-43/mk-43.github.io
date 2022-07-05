---
title: "[blog] LaTeX math"
excerpt: "Describe how to use math expression"

categories:
  - blog
tags:
  - [LaTeX]

toc: true
toc_sticky: true
use_math: true

date: 2022-04-19
last_modified_at: 2022-06-11
---

<https://en.wikibooks.org/wiki/LaTeX/Mathematics>  

Refer to [list](https://oeis.org/wiki/List_of_LaTeX_mathematical_symbols)  

$$  
    RMSE(X,h) = \sqrt{\frac{1}{m}{\sum_{i=1}^{m}{(h(x^{(i)})-y^{(i)})^2}}}  
$$  

$$  
    MAE(X,h) = \frac{1}{m}\sum_{i=1}^{m}{|{h(x^{(i)}) - y^{(i)}}|}  
$$  

Multiply, times  

$$  
    F1 = \frac{2}{\frac{1}{precision} + \frac{1}{recall}} = 2\times \frac{precision\times recall}{precision + recall}  
$$  

$$  
    \theta^{(\text{next step})} = \theta - \eta\nabla_{\theta}MSE(\theta)  
$$  

hat  

$$  
  \hat{p} = h_{\theta}(x) = \sigma(x^{T}\theta)  
$$  

$$  
\begin{equation}  
    \hat{y} = \begin{cases}  
        0 & \text{if}\ \hat{p} < 0.5 \\  
        1 & \text{if}\ \hat{p} \ge 0.5 \\  
    \end{cases}  
\end{equation}  
$$  

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
