---
title: "[NLP] Sentiment Detection"
excerpt: ""

categories:
  - sentiment
tags:
  - [nlp]

toc: true
toc_sticky: true

date: 2022-06-17
last_modified_at: 2022-07-21
---

주파수의 높낮이: pitch  
소리의 강도  

bitstream: 일반적으로 비트가 나열된 데이터  
3bit: 000, 001, 011, 111, ... -> 16개  

mono: 1채널  
stereo: 2채널  

16khz: (16bit로 표현된) 음이 초당 16,000개  

Loud HotAnger  
Calm ColdAnger  

Using prosody  

### sampling

the reduction of a continuous-time signal to a discrete-time signal  
a sound wave to a sequence of "samples"  
![image](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c3/Signal_Sampling.svg/600px-Signal_Sampling.svg.png)  

### sample

a value of the signal at a point in time  
a sample is taken at a particular time in the audio wave, recording **amplitude**.  
1 bit  

an audio sample: a number representing the measured acoustic wave value at a specific point in time.  

#### sampling rate(**sampling frequency**)

the average number of samples obtained in **one second**.  
e.g. 48 kHz = 48,000 samples per second  

### frequency

20Hz: 20 cycles **a second**  

### audio bit depth

the number of possible amplitude values  

16-bit: 65,356 values  
32-bit: 4,294,967,296 values  

### amplitude

the volume(얼마나 소리가 큰가 작은가)  

### MFCC

Mel-Frequency Cepstral Coefficient  
a representation of the short-term power spectrum of a sound,  
오디오에서 추출할 수 있는 피처로, 소리의 고유한 특징을 나타내는 수치  

### hamming

The hamming window reduces this ripple, giving you a more accurate idea of the original signal's frequency spectrum.  
[stackoverflow](https://stackoverflow.com/questions/5418951/what-is-the-hamming-window-for)  

#### Spectrum

#### Cepstrum

#### Mel Spectrum

### Speech-Emotion-Analyzer

https://github.com/MiteshPuthran/Speech-Emotion-Analyzer  

Classification problem ➜ CNN  

### An Audio Channel

the passage or communication channel in which a sound signal is transported from the player source to the speaker  
mono: one channel  
stereo: two or more channels  

## LabelEncoder

수치화(레이블링) 하여 데이터를 다룸  

## Fourier Series

주기함수는 기저함수(sin, cos)의 선형조합으로 표현  

#### 주기함수?

$$  
f(x+n*P) = f(x)  
$$  

벡터가 직교한다 ➜ 내적이 0이 된다  

함수 직교  

## Fourier transform

https://twlab.tistory.com/55  

## Fourier inversion

reconstruct the original wave  

## FFT

`n_fft(fft size)` 모든 주파수 성분을 계산하는 거싱 아니라 표본 개수를 정해 그만큼에 해당하는 영역만 계산  
가령, sr=44100, n_fft=32면, 0, 44100/(32/1), 44100/(32/2), ... , 44100/(32/16) 최대 sampling rate의 절반까지 n_fft 등분하여 계산  

## 위상

주기적인 현상에서 사이클상의 위치(radian으로 표시)  
