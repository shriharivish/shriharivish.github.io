---
layout: page
title: SHM
description: Time series analysis of structural sensor data
img: assets/img/shmp.png
importance: 11
category: fun
---


<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        .info-box {
            border: 2px solid #000000; /* Border color */
            padding: 20px; /* Padding inside the box */
            border-radius: 10px; /* Rounded corners */
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.5); /* Box shadow for a subtle lift */
            max-width: 800px; /* Maximum width of the box */
            text-align: center;
        }
        .info-box p {
            margin: 0; /* Remove default margin for better spacing */
        }
    </style>
</head>

<div class="info-box">
 <h4><b>Abstract</b></h4>
<p>
A tool providing Machine Learning and signal processing based algorithms 
for observation of a system over time using periodically sampled dynamic 
response measurements from an array of sensors. These tools aid in the extraction of
damage sensitive features in structures which are then statistically analysed. The tool was implemented on python.
</p></div> 
<br>

<h4>Signal Processing Methods</h4>
1. FFT; Custom Recursive Cooley FFT implementation from scratch and Cooley Tukey FFT implementation
from the numpy fft library.
2. CWT: Haar wavelet-based transforms implemented. Also performed signal reconstruction
and denoising using a successive DWT and IDWT implementation.

<h4>Methods of Smoothing</h4>
1. Moving Average
2. Exponential Smoothing
3. Trend Exponential Smoothing
4. Trend and Seasonal Exponential Smoothing
5. ARMA
6. ARIMA

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/bexp.png" title="Toolkit UI" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
   Toolkit UI; Exponential Smoothing Example
</div>