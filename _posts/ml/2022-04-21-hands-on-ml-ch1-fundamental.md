---
title:  "[ml] ch.2 End-to-End Machine Learning Project"
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

[1. Look at the big picture](#1-look-at-the-big-picture)

[2. Get the data](#2-get-the-data)

[3. Discover and visualizethe data to gain insights](#3-discover-and-visualizethe-data-to-gain-insights)

[4. Prepare the data for machine learning algorithms](#4-prepare-the-data-for-machine-learning-algorithms)

[5. Select a model and train it](#5-select-a-model-and-train-it)

[6. Fine-tune your model](#6-fine-tune-your-model)

[7. Present your solution](#7-present-your-solution)

[8. Launch, monitor, and maintain your system](#8-launch-monitor-and-maintain-your-system)


### 1. Look at the big picture

- Frame the problem  
  -\. know the business objective  

> **a data *pipeline***: a sequence of data processing components

- Select a performance measure
  - RMSE(Root Mean Square Error)
    - generally preferred performance measure for regression tasks
  - MAE(Mean Absolute Error)
$$
    RMSE(X,h) = \sqrt{\frac{1}{m}{\sum_{i=1}^{m}{(h(x^{(i)})-y^{(i)})^2}}}
$$
$$
    MAE(X,h) = \frac{1}{m}\sum_{i=1}^{m}{|{h(x^{(i)}) - y^{(i)}}|}
$$

outliers 많음 &rarr; MAE  
outliers 적음 &rarr; RMSE  
sqr가 들어가면서 큰 값은 더 커지고, 작은 값은 더 작아져서
 
 - check the assumptions

### 2. Get the data

- Take a quick look at the data structure  
- Create a test set
  - Don't do *data snooping*
  - typically 20% of the datset  
  - *strata*: homogeneous subgroups &rarr; *stratified sampling*
    - the test set should be representative of the overall population 

### 3. Discover and visualizethe data to gain insights

- Visualizing geographical data  
- Looking for correlations  
- Experimenting with attirbute combinations  

### 4. Prepare the data for machine learning algorithms

- Data cleaning  
  - one-hot encoding  
- Handling text and categorical attributes  
- Custom transformers  
- **Feature scaling**  
  - min-max scaling(normalization)  
  - standardization  

### 5. Select a model and train it

### 6. Fine-tune your model

### 7. Present your solution

### 8. Launch, monitor, and maintain your system
