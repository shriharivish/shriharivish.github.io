---
layout: page
title: Ultrasound
description: High fidelity low-power ultrasound fetal sensor
img: assets/img/uls.png
importance: 1
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
The ultrasound sensor is the very heart of GE’s fetal monitoring systems. It enables continuous monitoring and nonstress testing for the fetus in a clinical setting. I have worked on and delivered the soon-to-be-released portable fetal monitor, the successor to the Corometrics 250 series, which is the gold standard to date. Notably, we've achieved a significant breakthrough by successfully miniaturizing the entire Corometrics into the small sensor while improving on its performance. I am currently architecting next-generation wireless fetal sensors and systems for GE HealthCare, market leaders in the segment. Designed for safe and continuous monitoring, the sensor operates with extremely low acoustic outputs, thus requiring extremely high sensitivity to operate across diverse populations. I have also worked on enabling triplet and quadruplet monitoring, dealing with the complexity of multiple interchangeable sensors and crosstalk.
</p></div> 
<br>

LIMITED CONTRIBUTIONS LISTED BELOW DUE TO CONFIDENTIALITY REQUIREMENTS AT GE.

<br>

<h4>Transmit Section</h4>

Designed a new boost converter adapted transmit circuitry to optimise for power draw on the sensor. Used a charge pump mechanism to deliver consistent power output throughout the transmit pulse which drastically improves the sensitivity and lower depths. Tapering was a problem plaguing the predicate causing inconsistencies in the pickup at varied depths which was solved eventually in the new design. Optimised the circuit for space and ensured thermal loss was minimal given stringent heat dissipation requirements in an IP68 device. I have also designed the calibration process to ensure identical acoustic powers across sensors overcoming process variations in manufacturing.

<div class="img">
        {% include figure.html path="assets/img/uls_tx.jpg" title="Transmit Pulse Shape Improvement" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Transmit Pulse Shape Improvement
</div>



<h4>Recieve Section</h4>

The receive circuitry was drastically changed from the predicate as well. We introduced a tunable impedance element for maximising noiseless gain in the system and regularising gain across sensors despite manufacturing variabilities. The sensitivity was also improved drastically by redesigning the front end for low bias currents and higher input impedances preventing smaller signals from being dissipated. I introduced a new demodulation strategy for miniaturisation, performed gain rebalancing across the entire signal chain, optimised the RF amplifiers to accommodate the appropriate bandwidth, redesigned the high-order filters and introduced a mixer circuitry to accommodate for two channel sensing using one single ADC. I also drastically improved the noise performance of the sensor. 

<div class="img">
        {% include figure.html path="assets/img/uls_sensdpc.jpg" title="Sensitivity Improvement" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Sensitivity Improvement from Prototype and DoE to Demonstrate Performance
</div>

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        <div class="img">
            {% include figure.html path="assets/img/uls_senselec.png" title="Nanovolt Level Sensitivity" class="img-fluid rounded z-depth-1" %}
        </div>
        <div class="caption">
            Demonstrating Nanovolt Level Sensitivity
        </div>
    </div>
</div>


<h4>Clocking Section</h4>

Clock jitter is critical to performance of the ultrasound. Due to the way we demodulate in the RF domain, jitter can critically affect our noise levels as we even demodulate the directly reflected signals that are transmitted by the transducer. Jitter would mean we transmit one frequency and demodulate that very wave with a slightly different frequency giving rise to harmonics in our band of operation and thus an unwanted noise in our system. Need to meet jitter spec under 100ps given the sensitivity of the device. I’ve come up with an innovative low-cost low power solution to generate reconfigurable clock frequencies down to a 1Hz precision meeting the stringent jitter requirements of the system. This has majorly helped minimise all crosstalk effects.

<div class="img">
        {% include figure.html path="assets/img/uls_noise.png" title="Noise Levels" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Noise Levels Achieved in a High Gain System
</div>

<div class="img">
        {% include figure.html path="assets/img/uls_jitter.jpg" title="Jitter Improvement" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Jitter Improvement Demonstrating Picosecond Level Jitter
</div>


<h4>Crosstalk and Algorithms</h4>

Our crosstalk challenges involve intricacies such as the interplay of Nyquist theory in choosing frequencies. The need for tight tolerance in Pulse Repetition Rate (PRR) becomes crucial, as mismatched PRRs can generate unwanted signals. Imperfect frequency differences in modulation between transducers result in complex harmonics, emphasizing the necessity for tight frequency tolerance. Additionally, crosstalk with large signals can lead to clipping, causing a marginal reduction in sensitivity. I have come up with techniques to handle all these effects of having multiple transducers on a mother and have demostrated performance equivalence ith a single standalone sensor.


<div class="img">
        {% include figure.html path="assets/img/uls_crosstalksim.jpg" title="Simulation of Crosstalk" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Simulation of Crosstalk in the Downcoverter
</div>

I have designed the automatic gain control block in the DSP core of the microcontroller to help normalise the receive signal and make it easier for the heart rate algorithm to work. I also implemented a harmonic elimination technique using this very AGC I designed that helped solve a critical crosstalk problem. I have resolved major performance issues on the free-running frame-based autocorrelation algorithm and the control loop used to detect fetal movement. I have designed multiple low latency filters and developed other signal conditioning blocks like the envelope detector and the audio equaliser. 

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        <div class="img">
            {% include figure.html path="assets/img/uls_AGC.png" title="AGC" class="img-fluid rounded z-depth-1" %}
        </div>
        <div class="caption">
            Logarithmic Loop Automatic Gain Control Block
        </div>
    </div>
</div>

<div class="img">
        {% include figure.html path="assets/img/uls_dspfilters.jpg" title="Shaping Filters" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Low Latency Shaping Filters for Audio Response
</div>


<h4>Transducer Optimisation</h4>

To tackle process issues related to manufacturing of the transducer and the glueing involved I started modelling the PZT being used and the fully assembled transducer. Started out with fitting the FEM parameters using off the shelf PZT’s available publicly. Due to coupling of the radial and thickness mode there were considerable complexities in modelling. All parameters had to be fine tuned to match the measurements made in the lab. After assembly there was a significant change in the characteristics of the transducers because of the processes involved and the next stage was to model this. The plastics and glue were then integrated into the model next. This model was again tested with the assembled transducers and parameters were fine tuned here again. To understand the effect due to process variability of glueing, the thickness was varied, and the simulations were performed to evaluate performance across a large batch of manufactured transducers.

<div class="img">
        {% include figure.html path="assets/img/uls_gluemodel.jpg" title="Transducer Model" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    FEM Simulation with Varying Glue Thickness
</div>

Assuming a nominal thickness the complete transducer model was exported and then used to model the pressure sensitivity of the transducer and electro-mechanical interface. It was also used to model the transmit and receive sensitivity by using approximated mathematical models of the transmit and receive circuitry.

<div class="img">
        {% include figure.html path="assets/img/uls_modelsens.jpg" title="Pressure Sensitivity" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Pressure Sensitivity Simulation of Transducer
</div>

<div class="img">
        {% include figure.html path="assets/img/uls_elecmodel.jpg" title="Electrical Sensitivity" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Electrical Sensitivity Simulation Integrated with Transducer Sensitivity
</div>
