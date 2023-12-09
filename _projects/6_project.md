---
layout: page
title: PMB
description: Power management module for ventilators and anesthesia machines.
img: assets/img/ARC.png
importance: 6
category: fun
---

At the core of anaesthesia delivery machines and ventilators, the Power Management Board (PMB) assumes a pivotal role in supplying and monitoring power to critical machine components. Classified as Class A, the PMB demands a meticulously designed system, characterised by an extremely low margin for error. The Power Subsystem encompass the power management board, batteries, AC-DC module, power switch, and system cooling. The AC-DC module converts AC mains supply to regulated DC, while the Power Management Board, comprising both hardware and software, ensures uninterrupted power to other Darwin subsystems. Batteries serve as a backup power source, the Power Switch controls the enabling or disabling of power to the Darwin subsystems, and System Fans dissipate heat. I contributed to design fixes and debugging of the board.

LIMITED CONTRIBUTIONS LISTED BELOW DUE TO CONFIDENTIALITY REQUIREMENTS AT GE.

<div class="img">
        {% include figure.html path="assets/img/ARC_proto.jpg" title="Anaesthesia System" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Anaesthesia Delivery and Life Support Device
</div>

Anchored by the MSP432 microcontroller, the PMB oversees the intricate task of monitoring and controlling the input and output of the power supply subsystem. This includes scrutinizing and regulating power rails, allocating power to eight Safe Power Limit channels, and managing battery operations. Additionally, the PMB acts as a conduit for signal interfacing between the ventilation system, anaesthesia control system, and the display. I architected the communication framework for the entire system and created packets structures for all relevant communications. 

<div class="img">
        {% include figure.html path="assets/img/ARC_SWArch.png" title="Software Architecture" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Software Architecture
</div>

The power subsystem software is integral to monitoring and controlling power input and output for Darwin subsystems. It manages the switch positions, power supply during system startup and shutdown, battery operations, and temperature regulation through fan control. The software is structured into various units, with safety classifications for the Power subsystem Boot Code and Application. Temporal isolation segregates tasks, ensuring clarity and efficiency. Other software tasks, including vaporizer control, watchdog, battery charging, alarm management, IRIS communication, and system management, contribute to the overall functionality. RTOS synchronization modules facilitate inter-task communication and synchronization, enhancing the efficient functioning of the power subsystem software. I worked on all aspects of firmware on the PMB and refined the RTOS implementation to reduce power consumption and improve efficiency of the controller.

<div class="img">
        {% include figure.html path="assets/img/ARC_Arch.png" title="Test Software Architecture" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Test Software Architecture
</div>

Central to system communication, IRIS plays a crucial role in establishing point-to-point serial communication between subsystems. It also offers a standardized set of communication facilities for subsystem revision/status discovery and software upgrades. Our implementation utilizes a restricted version of IRIS, employing a low-level interface to the UART port for parsing and implementing the communication protocol. To complement PMB's functionality, the PMB tester tool package integrates a LabView based Windows application. This tool seamlessly interacts with the PMB, capturing inputs and displaying test results. Utilizing serial communication channels, the PC tool configures communication parameters, logs data, and establishes the operational mode of the PMB. This comprehensive testing framework ensures the robust functioning of the PMB within the broader system. Within the testing software framework, a user interface is designed to display monitored data and facilitate command inputs. The communication module, responsible for data transfer, accommodates both legacy and new virtual instruments. The Logging Engine processes and transmits string output from the global array to log files, complete with timestamps. Automation of requests within the testing software is executed through dedicated components. The software maintains inactive designs for potential upgrades, and the parameter changes guide offers comprehensive instructions for modifying receive components and configuration files. I worked on and single handedly developed the testing software end to end. The final prototype delivered effective communication and streamlined data processing within the system.


<div class="img">
        {% include figure.html path="assets/img/ARC_LabView.png" title="Test SW UI" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Test SW UI
</div>