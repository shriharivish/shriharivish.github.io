---
layout: page
title: SHM
description: Time series analysis of structural sensor data
img: assets/img/shm.png
importance: 8
category: fun
---

A tool providing Machine Learning and Signal Processing based algorithms 
for observation of a system over time using periodically sampled dynamic 
response measurements from an array of sensors. These tools aid in the extraction of
damage senstitive features in structures which are then statistically analysed.

Signal Processing Methods:
1. FFT; Custom Recursive Cooley FFT implementation from scratch and Cooley Tukey FFT implementation
from the numpy fft library.
2. CWT: Haar wavelet based transforms implemented. Also performed signal reconstruction
and denoising using a successive DWT and IDWT implementation.

Methods of Smoothing:
1. Moving Average
2. Exponential Smoothing
3. Trend Exponential Smoothing
4. Trend and Seasonal Exponential Smoothing
5. ARMA
6. ARIMA

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/bexp.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
   Toolkit UI; Exponential Smoothing Example
</div>