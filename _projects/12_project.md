---
layout: page
title: Chai-Tea
description: User friendly chai vending machine
img: assets/img/iic.png
importance: 12
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
In a society where working professionals grapple with hectic schedules, the demand for a quick and budget-friendly tea break is unmistakable. Existing tea vending machines often compromise on quality and affordability, particularly for middle-class families. The Chai-Tea vending machine addresses these concerns by offering authentic Indian tea preparation, promoting both health benefits and an appealing taste. What distinguishes it is its affordability, making it accessible to a broader demographic. This can also provide a convenient solution for the elderly, allowing them to enjoy a cup of tea with a simple press of a button. 
</p></div> 
<br>


<h4>Need Identification and Market Analysis</h4>
Started off with a market analysis and survey to help understand the potential of such an innovationm made estimations on the total addressable market, serviceable adressable market, revenue and profits. Followed on by analyzing the existing landscape of product offerings and alternatives, we took a closer look at the customer being addressed and the specific needs to be taken up for the prototype development. We also came up with a business model and ideated distribution channels to optimize for revenue and lower the cost of the product for the end user. 

<h4>High Level Architecture</h4>
The innovative setup of the tea vending machine incorporates a vertically movable filter that descends into the tea-making chamber, housing various components such as tea leaves, masala, sugar, water, and milk containers. Different pipes channel their contents into a funnel connected to the filter, initiating the tea-making process. The filter, once inside the container, facilitates proper heating of all ingredients. After 3-4 minutes, the filtering unit ascends, leaving only used tea leaves behind.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/iic_filter.png" title="Filter" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
   Filter Design on SolidWorks
</div>

<h4>Hardware Control</h4>
The machine's operation is orchestrated by a microcontroller, ensuring precision at each stage. From pumping water and regulating temperature to adding tea leaves, sugar, and masala with servo motors, the entire process is automated. The innovative aspects of the solution include the preparation of authentic tea, enhancing taste appeal. Moreover, the cost-effectiveness of the machine, to be priced at Rs. 3500, makes it accessible to middle-class families and beyond. Its widespread applicability caters to individuals from various demographics, including bachelors, couples, and the elderly, providing homemade tea with minimal effort.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/iic_system.png" title="System Design" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
   System Design for Vending Machine
</div>

<h4>Automation</h4>
The impact of the solution extends to addressing prevalent issues in the tea consumption landscape. It tackles the wastage of time and energy in manual tea preparation, health concerns related to vending machine tea, dissatisfaction with taste, and the absence of affordable and user-friendly household vending machines. By automating the tea-making process, the solution aligns with the preferences and lifestyles of a large section of modern society, aiming to revolutionize the tea consumption experience for millions.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/iic_circuit.png" title="Hardware Architecture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
   Hardware Architecture for Vending Machine
</div>