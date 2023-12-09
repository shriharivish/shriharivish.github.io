---
layout: page
title: PPG
description: Miniturized biosensor for arrhythmia diagnosis
img: assets/img/ceeri.jpg
importance: 3
category: work
---

A miniature (for a wrist watch form factor) Reflective Photoplethysmography module developed at Dr. Bala Pesala’s lab at CSIR-CEERI Chennai to enable arrhythmia detection in resource constrained settings.

With the advent of healthcare technologies, portability of health-care devices is a major concern. One such healthcare device is an Electrocardiograph monitor which requires electrodes in contact with the body. However, it is not portable and often causes skin irritation on continued use. This project aims at innovating a non-contact electrode system to monitors the user's Heart Rate, Heart Rate Variability and pulsatile flow of blood in arteries. The long-term goal of the watch is to help diagnose arrhythmia and detect the causes of fatigue in the user. 

<div class="img">
        {% include figure.html path="assets/img/ceeri_spectrum.jpg" title="Spectral Analysis" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Spectral Analysis of Sensor
</div>

We chose photoplethysmography as the technique for cost-effective non-invasive monitoring. and chose the OSRAM SFH7050 as the base sensor to work on. Started off with a spectral analysis of the sensor's three LEDs and the photodiodes to understand the closed loop response in an ideal setup. Next, I built a simple amplifier circuitry to help us probe the raw signal recieved on each channel and help us experiemnt by measuring signals from our own bodies. Understanding the need to isolate various frequencies from the raw signal to extract different information form the raw signal I went on to design various digital filters to help us understand what response would be valuable for our pursuit.

<div class="img">
        {% include figure.html path="assets/img/ceeri_individualresponses.jpg" title="Signal Responses" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Individual Signal Responses
</div>

To improve sensitivity of the electronics I designed a transimpedance amplification circuitry to minimize bias current requirements and then added an extra gain stage to get a signal output that can be read by low power ADC's. Then I designed high order bandpass and notch filters to remove the unwanted frequencies and noises being transmitted through the signal chain. I used multifeedback bandpass filter due to the space constraints we faced and to maximize the effect of filtering. The 50Hz powerline noise in the system was overwhelming the signal and I had to design a twin-t notch filter to maximise the attenuation of 50Hz and 60Hz noise to generate a clean signal finally. Given the low sampling rates of most low power ADC's using digital filtering to remove this noise was going to be tricky too. 

<div class="img">
        {% include figure.html path="assets/img/ceeri_breadboard.jpg" title="Breadboard Prototype" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Breadboard Prototype
</div>

<div class="img">
        {% include figure.html path="assets/img/ceeri_finalsignal.jpg" title="Signal Captures & SpO2 Measurement" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Signal Captures & SpO2 Measurement
</div>

After implementing a proof-of-concept on the breadboard I designed my first ever PCB on Altium and independently chose a fab house, interacted with the manufacturer, transfer the design, got it optimized and manufactured the PCB to deliver a wrist watch sized device.

<div class="img">
        {% include figure.html path="assets/img/ceeri_pcba.jpg" title="PCB" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    PCB
</div>

We also used pulse oximetry (using PPG readings of two wavelengths) to find the saturated oxygen content in the blood to help identify fatigue. A common problem in pulse-oximetry is the decreased accuracy for individuals with a dark skin, especially the overestimation of SpO2 during de-saturation. Because of the higher melanin content of their skin, more visible light is absorbed (not IR), resulting in reflected light with a lower pulsatile amplitude compared to skin with a lower pigmentation level. To tackle the issue of varying pigmentation levels across users we came up with a method to simultaneously transmit and measure DC and AC reflectances. This is because both the AC and DC components decrease for increasing melanin content, the ratio of both remains stable, resulting in a stable signature-vector over the entire range of skin pigmentation level. As a result, the calibration coefficients for the SpO2 calculations are expected to be independent of the skin pigmentation level and provide an inclusive experience to diverse users.