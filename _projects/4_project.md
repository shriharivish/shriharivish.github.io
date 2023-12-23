---
layout: page
title: Incubation
description: Accelerating culture experiments at TranslaTUM
img: assets/img/tum.jpg
importance: 4
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
Culture is the process where a fragment of biomatter is forced to grow or develop in a tertiary
medium. Tissue and cell culture are helping pave the way for numerous technological breakthroughs
and the work aims to improve the efficiency with which experiments are conducted. I conducted this research at Dr. Oliver Hayden's lab for biomedical electronics as part of my bachelor's thesis at TranslaTUM, TU Munich, Germany. AT TranslaTUM,
this research is primarily going to accelerate cancer drug testing and cell model studies. I constructed a chamber equipped with necessary actuation mechanisms using the Opentrons OT-2. Subsequently, I implemented a real-time feedback sensing system for monitoring ambient parameters. I collaborated with Sendsor GmbH on their prototype flow-based CO2 sensor. Finally, I integrated the entire system with a MIMO control system, and optimized system parameters to achieve a fivefold increase in assay throughput.
</p></div> 
<br>

<h4>The Pipetting Robot</h4>

The OT-2 from Opentrons is an affordable, easy-to-use pipetting robot that uses
integrated electronic pipettes to transfer liquids and run experiments. The vision was to build a system where
incubating a sample for tissue or cell culture would be possible simultaneously after the 
pipetting is done or alongside the pipetting, all remotely. I installed the newly acquired system and got
it up and running. I also wrote multiple scripts to help automate pipetting experiments in the lab.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/tum_ot2.png" title="Opentrons OT2" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Opentrons OT2
</div>

<h4>Incubation - Temperature</h4>

An incubator is best represented by a human body in terms of the
ambient conditions required to help cells and tissues grow. The most
important factor thus is temperature. The space required to implement
the additional devices for creating an incubator was restricted due to the
movement of the robot’s arm. An 800W heater was needed to achieve
the specified temperature requirement and maintain the control loop
within the prescribed margin. Given the constraints, a ceramic thin plate
heater was chosen. I also chose suitable materials and fabricated a rugged mounting
mechanism to withstand and isolate the heat over long durations.
I thereafter, architected the circulation system for even distribution of
heat in the chamber.


<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/tum_heater.png" title="Architecture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Heating Architecture and Mounting Mechanism
</div>

<h4>Incubation - Humidity</h4>

The next parameter to be addressed was humidity control so as to
preserve the osmolarity of the culture samples. To achieve this glass
washing flasks were used. Gas washing flasks are used to wet/ humidify gases by exposing
them to water. When the gas from the inlet pipe reaches the bottom of a filled flask it rises up
in bubbles and along the way picks up water particles and then exits via the exit pipe. In
principle, it is almost the same as a water bath humidifier. I implemented the arrangement using a
vacuum gas pump that pumped the gas to the bottom of the water filled
flask. By suitably designing the flow rate and quantity of water used, humidity in the incubator 
can be controlled. A three-flask configuration in series was designed to maximise the efficiency of the system.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/tum_humidity.png" title="Humidity Control" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Humidity Control
</div>

<h4>Incubation - CO2</h4>

The last control implemented was for CO2 in the chamber. I worked with SENDSOR Gmbh, a Munich based startup, to integrate their flow based CO2 sensor into the chamber for implementing the closed loop control. The initial testing of the sensor integrated with the control system was undertaken at the SENDSOR headquarters. I created an inlet in the chamber
and added an electronically controlled pneumatic switch to control the flow of CO2 into the chamber.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/tum_sendsor.png" title="SENDSOR Gmbh Prototype" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    SENDSOR Gmbh Prototype
</div>

<h4>Control System</h4>

Finally, I integrated the sub-systems onto an Arduino and implemented
a multi-parametric PID control loop with inter-dependent variables. This
complex implementation within constrained timelines required a good
amount of effort to fine-tune the system. I was able to demonstrate the
performance of the incubator and control system within the assigned
duration of my time in Germany. Other than my thesis work,
I also wrote scripts to help others automate their work on the Opentrons
and was the first person to get the system up and running. 

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/tum_pid.jpg" title="PID Control" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Multiparametric PID Control on Arduino
</div>

