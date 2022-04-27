---
title:  "[ml] ch.3 Classification"
excerpt: ""

categories:
  - ml
tags:
  - [hands-on, classification]

toc: true
toc_sticky: true
 
use_math: true
date: 2022-04-26
last_modified_at: 2022-04-26
---

### Training a binary classifier

Stochastic Gradient Descent (SGD) Classifier
- well suited for online learning

### Performance measures

#### Measuring accuracy using cross-validation

#### confusion matrix

count the number of times instances of class A are classified as class B

*precision*: the accuracy of the positive predictions
$$
    precision = \frac{TP}{TP+FP}
$$
where TP is the number of true positives, and FP is the number of false postivies.

*recall(sensitivity, or true positive rate(TPR)*: the ratio of positive instances that are correctly detected by the classifier
$$
    recall = \frac{TP}{TP+FN}
$$

*F1 score*: harmonic mean of precision and recall  
*harmonic mean* gives much more weight to low value  
Thus, both reacll and precision &uarr; &rarr; F1 &uarr;
$$
    F1 = \frac{2}{\frac{1}{precision} + \frac{1}{recall}} = 2\times \frac{precision\times recall}{precision + recall}
$$

### ROC curve

Receiver Operating Characteristic curve plots the *true positive rate(recall)* against *false positive rate (FPR)*

$$
  FPR = 1 - \frac{1}{\text{true negative rate (TNR)}}
$$

FPR: the ratio of negative instances that are incorrectly classified as **positive**  
TNR(specificity): the ratio of negative instances that are correctly classified as **negative**

the ROC curve plots *sensitivity(recall)* versus 1-*specificity*

AUC: Area Under the Curve

### Multiclass classification

can distinguish between more than two classes  
Multiclass algorithms: SGD classifiers, Random Forest classifiers, and naive Bayes classifiers  
Binary classifiers: Logistic Regression, SVM

*one-versus-the-rest* (OvR): train 10 binary clasifiers and pick one whose classifier outputs the highest score.

*one-versus-one* (OvO): train a binary classifier for every pair of digits($N\times(N-1) / 2$)  


### Multilabel classification

outputs multiple binary tags

### Multioutput classification

each label can be multiclass
