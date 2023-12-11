---
layout: page
title: Novii
description: Patch based fetal monitoring system
img: assets/img/nv.png
importance: 2
category: work
---

The Novii Monitoring System includes the Novii Patch, a disposable adhesive patch with five electrodes attached to the mother's abdomen. It features a magnetic cradle at its center for the Novii Pod. The Novii Pod, a battery-operated device with Bluetooth and Infrared connectivity, processes signals from the patch to provide Maternal Heart Rate, Fetal Heart Rate, and Uterine Activity. Acting as a wireless bridge, the Novii Interface Module transmits patient data between the Pod and the fetal monitor. The Standalone Pod Charger efficiently charges two Novii+ pods simultaneously, enhancing user convenience. 

LIMITED CONTRIBUTIONS LISTED BELOW DUE TO CONFIDENTIALITY REQUIREMENTS AT GE.

<div class="img">
        {% include figure.html path="assets/img/NV_Lotus.png" title="Novii System" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Novii Pod and Peripheral Devices
</div>

Designed a Qi compliant dual smart charger for the Novii Pods. Implemented the charging circuitry, foreign object detection with compensation for losses from the pod, and finetuned the vertical stack up and coil to reduce losses. Used magnets on the pod and a hall elect sensor to implement docking detection on the charging bays. Multiple safety features were introduced to prevent any harm in case of overtemperatures or malfunctions. 

<div class="img">
        {% include figure.html path="assets/img/nv_spc.jpg" title="SPC" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Wireless Charger Board
</div>

Designed an IR and Bluetooth module for enabling seamless communication between the Novii pods and next generation fetal monitors. Ensured miniaturisation of the interface and thermal performance given high data rates being used to transmit information wirelessly. Solved issues with IR pairing ranges due to attenuating media, Bluetooth range of communication, and LED driver optimization for reducing current consumption.

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        <div class="img">
            {% include figure.html path="assets/img/nv_nim.jpg" title="NIM" class="img-fluid rounded z-depth-1" %}
        </div>
        <div class="caption">
            IR-Bluetooth-USB Interface
        </div>
    </div>
</div>

Part of the team that introduced the algorithm improvement to include pre term labour monitoring for the Novii line of products. The fetal heart rate counting algorithm was improved and signal conditioning blocks were optimized. Also contributed heavily to the biostatistical analyses and the clinical trials to prove the efficacy of the improved Novii (510k). Improved the hardware by implementing a power reduction technique using sleep mode and added an accelerometer to trigger wakeup.
        {% include figure.html path="assets/img/NV_Trials.png" title="Clinical Trials" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Clinical Trials
</div>

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        <div class="img">
            {% include figure.html path="assets/img/NV_Trials.png" title="Clinical Trials" class="img-fluid rounded z-depth-1" %}
        </div>
        <div class="caption">
            Clinical Trials
        </div>
    </div>
</div>

I have contributed to various regular engineering activities. I helped design the automated test equipment for the manufacturing line, completed vitality analyses and made cost improvements to the bill of materials. I also interacted with suppliers and customers regularly to solve issues on the line and in the field.

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        <div class="img">
            {% include figure.html path="assets/img/NV_ATE.jpg" title="ATE" class="img-fluid rounded z-depth-1" %}
        </div>
        <div class="caption">
            Automated Test and Calibration Equipment
        </div>
    </div>
</div>


The internship project involved integrating Near Field Communication (NFC) and Bluetooth for wireless data exchange. NFC enables secure close-range transactions to facilitate Bluetooth pairing to enable broader connectivity. Implemented using Arduino, HC-05 Bluetooth modules, and the PN532 NFC reader/writer, the model comprises three Arduinos, three Bluetooth modules, two NFC tags, and one NFC reader. I successfully demonstrated the feasibility and improved functionality of the pods, thus influencing future roadmaps to incorporate Bluetooth Low Energy (BLE) for energy efficiency, exploring Out-of-Band (OOB) pairing for security, and data encoding for increased privacy. 


<div class="img">
        {% include figure.html path="assets/img/NV_InternWorkflow.PNG" title="Workflow" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Workflow for Smart Sensor Pairing
</div>