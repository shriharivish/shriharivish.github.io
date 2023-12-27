---
layout: page
title: Glaucoma
description: Neural networks for glaucoma diagnosis
img: assets/img/kk.jpg
importance: 7
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
Glaucoma diagnosis is very complex and can go wrong at multiple steps. Even seasoned ophthalmologists can make mistakes and overlook signs. Glaucoma is extremely prevalent in the world and is one of the leading causes of vision loss and blindness. Automating the identification will help with timely diagnosis helping many people to save their vision. The analysis of the fundus images of the retina is the method chosen because fundus images are easiest to capture and fundus cameras are easily affordable. The use of neural networks is to generalize predictions and to completely automate the process of preliminary diagnosis. I have worked on pre-processing techniques, building the pipeline and the CNN implementation of the network being used.
</p></div> 
<br>


<h4>Needs Identification</h4>

The best way to tackle a problem with multiple needs is to choose the most important ones and work with them. Thus, we developed a Value Proposition Chart working with Dr. Jigish Gandhi (Ophthalmologist) and Dr. V. Premnath (Chief Scientist, NCL and Director, NCL Venture Center) to understand the pressing needs to be addressed. 

<div class="img">
        {% include figure.html path="assets/img/kk_value.png" title="Value Proposition Chart" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Value Proposition Chart
</div>


<h4>Pre-Processing</h4>

The original image has been downsized and regularized to 224*244 size images for easier and faster operation. In the image, the parts of the fundus image that aren’t relevant have been cropped out, the disc and some area surrounding it, which has the most number of features to help identify glaucoma have been retained. This is helpful as the model will train with only relevant data making the model more suited for our use. Further we have performed gamma correction and noise removal.

<div class="img">
        {% include figure.html path="assets/img/kk_proc.png" title="Pre-processing" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Pre-processing and Trimming
</div>


<h4>Model Implementation</h4>

The network has been grouped into three parts consisting of two, two and three convolutional layers separated by max pool layers between them. The features obtained after the seventh convolutional layer have been flattened and densed into a 1000-dimensional layer. This layer is used by the sigmoid function for the binary classification. The number of strides on the convolutional layers have been set to two with additional padding to the prevent loss of features. Relu activation function has been used for non-linearization of the feature vector and helps in faster learning as it can easily backpropagate the errors and have a constant gradient. Max pooling layers have been used to reduce the spatial size of the feature vector. In doing so the max pooling layers reduce the number of parameters and reduce the computational time and space of the following layers.

<div class="img">
        {% include figure.html path="assets/img/kk_nn.jpg" title="Neural Network Implementation" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Neural Network Implementation
</div>

<h4>Model Performance</h4>

The model has been trained using the binary cross entropy loss function. The model has been trained on a total of 410 images out of which 180 are images of glaucoma-ridden eyes and 230 are glaucoma free. Then, the model was tested on 45 images. Out of the 45 images in the testing set, 25 are normal and 20 are affected.


<div class="img">
        {% include figure.html path="assets/img/kk_graph.png" title="Accuracy" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Accuracy Over Time at Different Training Sensitivities
</div>

<div class="img">
        {% include figure.html path="assets/img/kk_table.png" title="Sensitivity and Specificity" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Sensitivity and Specificity Values
</div>
