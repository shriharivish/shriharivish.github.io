---
layout: page
title: Ultrasound
description: High fidelity low-power ultrasound fetal sensor
img: assets/img/ultrasound.JPG
importance: 1
category: work
---

The ultrasound sensor is the very heart of GE’s fetal monitoring systems. It enables continuous monitoring and nonstress testing for the fetus in a clinical setting. It is responsible for the generation of the Transmit Acoustic Signal, receiving the reflected signal from one of the fetuses, as well as the processing of the signal, determination of the fetal heart rate, and finally the transmission of the fetal heartbeat information to the fetal monitor digitally. The module is a low power sensor designed to be operated continuously for over a day because of which the transmit power of the ultrasound needed to be very low. High transmit powers can lead to heating of tissues potentially harming the mother and the baby. The major complexity of design here is driven by sensitivity given the low acoustic output coupled with the acoustic attenuation due to human skin, fat and the interface. The other complexity is that this is a multiple transducer system leading to various types of crosstalk causing signal confusion, interference, and noise. We have also performed extensive miniaturisation of the electronics to accommodate all the electronics in this small sensor instead of the large Corometrics device.

LIMITED CONTRIBUTIONS LISTED BELOW DUE TO CONFIDENTIALITY REQUIREMENTS AT GE.

<div class="img">
        {% include figure.html path="assets/img/uls_tx.JPG" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Segmentation results
</div>

Designed a new boost converter adapted transmit circuitry to optimise for power draw on the sensor. Used a charge pump mechanism to deliver consistent power output throughout the transmit pulse which drastically improves the sensitivity and lower depths. Tapering was a problem plaguing the predicate causing inconsistencies in the pickup at varied depths which was solved eventually in the new design. Optimised the circuit for space and ensured thermal loss was minimal as heat dissipation was a problem due to the IP68 requirements of the sensor.

<div class="img">
        {% include figure.html path="assets/img/uls_sensdpc.JPG" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Segmentation results
</div>

<div class="img">
        {% include figure.html path="assets/img/uls_senselec.png" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Segmentation results
</div>

The receive circuitry was drastically changed from the predicate as well. We introduced a tunable impedance element for maximising noiseless gain in the system and regularising gain across sensors despite manufacturing variabilities. The sensitivity was also improved drastically by redesigning the front end for low bias currents and higher input impedances preventing smaller signals from being dissipated. I introduced a new demodulation strategy for miniaturisation, performed gain rebalancing across the entire signal chain, optimised the RF amplifiers to accommodate the appropriate bandwidth, redesigned the high-order filters and introduced a mixer circuitry to accommodate for two channel sensing using one single ADC. I also drastically improved the noise performance of the sensor. 

<div class="img">
        {% include figure.html path="assets/img/uls_noise.png" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Segmentation results
</div>

<div class="img">
        {% include figure.html path="assets/img/uls_jitter.JPG" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Segmentation results
</div>

Clock jitter is critical to performance of the ultrasound. Due to the way we demodulate in the RF domain, jitter can critically affect our noise levels as we even demodulate the directly reflected signals that are transmitted by the transducer. Jitter would mean we transmit one frequency and demodulate that very wave with a slightly different frequency giving rise to harmonics in our band of operation and thus an unwanted noise in our system. Need to meet jitter spec under 10ps given the sensitivity of the device.
Crosstalk 1: Based on the Nyquist theory, our receive demodulation’s RF sampling rate and our modulation frequency are interrelated. Now, our three frequencies must be chosen so that our difference between any two of them is never a multiple of the RF sampling rate.
Crosstalk 2: During crosstalk, when a second transducer's transmit wave is being received by our transducer, if the PRR’s are different, we will see the pulse slide across the receive period causing signals being generated in the frequency of the difference in the PRR’s. Thus, the PRR must have a tight tolerance.
Crosstalk 3: Like crosstalk scenario 2, if the difference in the frequencies of modulation between multiple transducers is not perfect, it will lead to complex harmonics that when passed through our main filter will give us remnants in the 100-300Hz range (FHR Bandwidth). This necessitates the requirement of tight tolerance on frequencies being used for modulation and demodulation.
Crosstalk 4: During crosstalk of large signals, the LC tank output would get saturated and would cause clipping. During this clipping if a small receive signal of interest is received there would be some signal loss and would cause a marginal reduction in sensitivity. Not clinically relevant due to attenuation caused by the human body.
I’ve come up with an innovative low-cost low power solution to generate reconfigurable clock frequencies down to a 1Hz precision meeting the stringent jitter requirements of the system. This has majorly helped minimise all crosstalk effects. 

<div class="img">
        {% include figure.html path="assets/img/uls_crosstalksim.JPG" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Segmentation results
</div>

<div class="img">
        {% include figure.html path="assets/img/uls_AGC.png" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Segmentation results
</div>

<div class="img">
        {% include figure.html path="assets/img/uls_dspfilters.JPG" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Segmentation results
</div>

I have designed the automatic gain control block in the DSP core of the microcontroller to help normalise the receive signal and make it easier for the heart rate algorithm to work. I also implemented a harmonic elimination technique using this very AGC I designed that helped solve a critical crosstalk problem. I have resolved major performance issues on the free-running frame-based autocorrelation algorithm and the control loop used to detect fetal movement. I have designed multiple low latency filters and developed other signal conditioning blocks like the envelope detector and the audio equaliser. 

<div class="img">
        {% include figure.html path="assets/img/uls_gluemodel.JPG" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Segmentation results
</div>

To tackle process issues related to manufacturing of the transducer and the glueing involved I started modelling the PZT being used and the fully assembled transducer. Started out with fitting the FEM parameters using off the shelf PZT’s available publicly. Due to coupling of the radial and thickness mode there were considerable complexities in modelling. All parameters had to be fine tuned to match the measurements made in the lab. After assembly there was a significant change in the characteristics of the transducers because of the processes involved and the next stage was to model this. The plastics and glue were then integrated into the model next. This model was again tested with the assembled transducers and parameters were fine tuned here again. To understand the effect due to process variability of glueing, the thickness was varied, and the simulations were performed to evaluate performance across a large batch of manufactured transducers.

<div class="img">
        {% include figure.html path="assets/img/uls_modelsens.JPG" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Segmentation results
</div>

<div class="img">
        {% include figure.html path="assets/img/uls_elecmodel.JPG" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Segmentation results
</div>

Assuming a nominal thickness the complete transducer model was exported and then used to model the pressure sensitivity of the transducer and electro-mechanical interface. It was also used to model the transmit and receive sensitivity by using approximated mathematical models of the transmit and receive circuitry.
