---
layout: page
title: Incubation
description: Accelerating culture experiments at TranslaTUM
img: assets/img/tum.jpg
importance: 2
category: work
---

Culture is the process where a fragment of biomatter is forced to grow or develop in a tertiary
medium. Tissue culture is of various types based and is classified based on the originating 
fragment. Tissue and cell culture are helping pave the way for numerous technological breakthroughs
and the aim of the thesis is to improve the efficiency with which experiments are conducted. AT TranslaTUM,
this research is primarily gong to be used to perform rapid cancer drug testing and cell model studies.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/tum_ot2.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Opentrons OT2 Pipetting Robot
</div>

The OT-2 from Opentrons is an affordable, easy-to-use pipetting robot that uses
integrated electronic pipettes to transfer liquids and run experiments. The vision was to build a system where
incubating a sample for tissue or cell culture would be possible simultaneously after the 
pipetting is done or alongside the pipetting, all remotely. 

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/tum_heater.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Heating Architecture and Mounting Mechanism
</div>

An incubator is best represented by a human body in terms of the ambient conditions required to help cells
and tissues grow. The most important factor thus is temperature. The design of the system was extremely
constricted due to the movement of the robot’s arm. A heater generating over 800W would have to be used to
be able to reliably run the control loop with margin. Given size constraints, we finally found one suitable option,
a ceramic thin plate heater. I designed and manually fabricated the mounting mechanism with reliable materials with 
proven resistance to heat and durability at high temperatures. I also architected the circuilation system for even
distribution of heat in the chamber.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/tum_humidity.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Humidity Control
</div>

The next parameter we took on was the humidity to preserve the osmolarity of the samples being cultures, especially
given the heating mechanism in place. Gas washing flasks are used to wet/ humidify gases by exposing
them to water. When the gas from the inlet pipe reaches the bottom of a filled flask it rises up
in bubbles and along the way picks up water particles and then exits via the exit pipe. In
principle, it is almost the same as a water bath humidifier. The amount of water and the flow
rate are key factors that affect the resulting humidity of the system. I implemented various configurations with
best performance achieved with three flasks in series being driven by a vaccum gas pump. 

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/tum_sendsor.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    SENDSOR Gmbh Prototype
</div>

The last control implemented was for CO2 in the chamber. I worked with SENDSOR Gmbh to integrate their flow based
CO2 sensor into the chamber for implementing closed loop control of the same. We ran intial testing of the sensor and
my integrated system for the CO2 level readout at the SENDSOR headqurters in Munich. I created an inlet in the chamber
and a electronically controlled pneumatic switch to control when the CO2 would flow into the chamber for control.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/tum_pid.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Multiparametric PID Control on Arduino
</div>

FInally, I integrated all the actuation subsystems onto a single Arduino and then implemented a multiparametric control
loop with interdependent variables. This was quite complex to implement but after carefully finetuning the control system
I was able to close my work at TranslaTUM and run experiments for the group before my time in Germany came to an end. Other than my thesis work, I also wrote scripts to help others automate their work on the Opentrons and was the first person to get the
system up and running. 