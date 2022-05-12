---
title: "[perfect guide] text mining "
excerpt: ""

categories:
  - ml
tags:
  - [perfect-guide]

toc: true
toc_sticky: true
use_math: true

date: 2022-04-28
last_modified_at: 2022-05-12
---

## 텍스트 분석의 개요

### 텍스트 전처리 - 텍스트 정규화

- cleansing
  - 텍스트 분석에 방해가 되는 불필요한 문자, 기호 제거(HTML, XML tag)
- tokenization
  - 문장 토큰화
  - 단어 토큰화
  - n-gram
- 필터링/스톱워드 제거/철자 수정
  - 불필요한 단어나 분석에 큰 의미가 없는 단어(전치사 등) 제거, 잘못 된 철자 수정
- Stemming/Lemmatization
  - 어근(단어 원형) 추출
  - 의미론적 기반에서 단어 원형을 찾음

### N-gram

문장을 개별 단어 별로 하나씩 토큰화 할 경우 문맥적인 의미가 무시될 수 있다.  
n-gram은 연속된 n개의 단어를 하나의 토큰화 단위로 분리하는 것.  
n개 단어로 윈도우를 만들어 토큰화 수행  

Agent Smith knocks the door  
`Agent Smith` `Smith knocks` `knocks the` `the door`  

### NLTK
