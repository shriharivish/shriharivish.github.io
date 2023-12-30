---
layout: page
title: PPG
description: Miniturized biosensor for arrhythmia diagnosis
img: assets/img/ceeri.jpg
importance: 3
category: work
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
            text-align: left;
        }
        .info-box p {
            margin: 0; /* Remove default margin for better spacing */
        }
    </style>
</head>

<div class="info-box">
 <h4><b>Abstract</b></h4>
<p>
During my undergraduate internship, I worked on the development of a miniature (for a wrist watch form factor) Reflective Photoplethysmography module developed at Dr. Bala Pesala’s lab at CSIR-CEERI Chennai to identify causes of fatigue and diagnose arrhythmia in resource constrained settings. With the advent of healthcare technologies, portability of health-care devices is an important requirement for ensuring patient comfort and accessibility. The project resulted in an non-contact-electrode system for monitoring Heart Rate, Heart Rate Variability, and pulsatile blood flow in arteries. Unlike traditional Electrocardiograph monitors, the photoplethysmography based system eliminates the need for direct contact with the body, addresses portability concerns and reduces the risk of skin irritation during prolonged use. I worked on designing the front end, charachterizing the photodiodes and recievers, fabricating the electronic board and developing the digital signal processing blocks involved.
</p></div> 
<br>

<h4>Optical Charachterization</h4>

We chose photoplethysmography as the technique for cost-effective non-invasive monitoring. and chose the OSRAM SFH7050 as the base sensor to work on. Started off with a spectral analysis of the sensor's three LEDs and the photodiodes to understand the closed loop response in an ideal setup. Next, I built a simple amplifier circuitry to help us probe the raw signal received on each channel and help us experiment by measuring signals from our own bodies. In order to extract the required information from the raw signal, I isolated and tried to understand the different frequencies of interest in the raw signal. Thereafter, I designed digital filters to extract the signals that were of interest to us.

<div class="img">
        {% include figure.html path="assets/img/ceeri_spectrum.jpg" title="Spectral Analysis" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Spectral Analysis of Sensor
</div>

<h4>Analog Design</h4>

To improve sensitivity of the electronics I designed a transimpedance amplification circuitry to minimize bias current requirements and then added an extra gain stage to get a signal output large enough to be sampled by an ADC. Then I designed high order bandpass and notch filters to remove the unwanted frequencies and noises being transmitted through the signal chain. I used multi-feedback bandpass filter due to the space constraints we faced and to maximize the effect of filtering. The 50Hz powerline noise in the system was overwhelming the signal and I had to design a twin-t notch filter to maximise the attenuation of 50Hz and 60Hz noise to generate a clean signal finally. Given the low sampling rates of most low power ADC's, using digital filtering to remove this noise was complex as well. 

<div class="img">
        {% include figure.html path="assets/img/ceeri_individualresponses.jpg" title="Signal Responses" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Individual Signal Responses
</div>

<div class="img">
        {% include figure.html path="assets/img/ceeri_breadboard.jpg" title="Breadboard Prototype" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Breadboard Prototype
</div>


<h4>PCB</h4>

After implementing a proof-of-concept on the breadboard I designed my first ever PCB on Altium and independently chose a fab house, interacted with the manufacturer, transferred the design, got it optimized and manufactured the PCB to deliver a wrist watch sized device.

<div class="img">
        {% include figure.html path="assets/img/ceeri_pcba.jpg" title="PCB" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    PCB
</div>

<h4>SpO2 Monitoring</h4>

We also used pulse oximetry (using PPG readings of two wavelengths) to find the saturated oxygen content in the blood to help identify fatigue. A common problem in pulse-oximetry is the decreased accuracy for individuals with a dark skin, especially the overestimation of SpO2 during de-saturation. Because of the higher melanin content of their skin, more visible light is absorbed (not IR), resulting in reflected light with a lower pulsatile amplitude compared to skin with a lower pigmentation level. To tackle the issue of varying pigmentation levels across users we came up with a method to simultaneously transmit and measure DC and AC reflectances. This is done since the AC and DC components decrease for increasing melanin content, while their ratio remains same. This ratio ensures that the signature vector gives a realistic value of SpO2. As a result, the calibration coefficients for the SpO2 calculations are expected to be independent of the skin pigmentation level and provide an inclusive experience to diverse users.

<div class="img">
        {% include figure.html path="assets/img/ceeri_finalsignal.jpg" title="Signal Captures & SpO2 Measurement" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Signal Captures & SpO2 Measurement
</div>