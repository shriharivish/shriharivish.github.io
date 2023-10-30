---
layout: page
title: Glaucoma
description: Neural networks for Glaucoma diagnosis
img: assets/img/covaid.png
importance: 5
category: fun
---

Glaucoma diagnosis is very complex and can go wrong at multiple steps. Even seasoned ophthalmologists can make mistakes and overlook signs. Glaucoma is extremely prevalent in the worldand is one of the leading causes of vision loss and blindness. Automating the identification will help with timely diagnosis helping many people to save their vision. The analysis of the fundus images of the retina using neural network is the method chosen because fundus images are easiest to capture and fundus cameras are easily affordable.

<div class="img">
        {% include figure.html path="assets/img/kk_value.png" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Value Proposition Chart
</div>

The best way to tackle a problem with multiple needs is to choose the most important ones and work with them. Thus, we developed a Value Proposition Chart working with Dr. Jigish Gandhi (Ophthalmologist) and Dr. V. Premnath (Principal Scientist, NCL and Director, NCL Venture Center) to understand the pressing needs to be addressed. 

<div class="img">
        {% include figure.html path="assets/img/kk_proc.png" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Pre-processing and Trimming
</div>

The original image has been downsized and regularized to 224*244 size images for easier and faster operation. In the image, the parts of the fundus image that aren’t relevant have been cropped out, the disc and some area surrounding it, which has the most number of features to help identify glaucoma have been retained, this is very helpful as the model will train with only relevant data making the model more suited for our use. Further we have performed gamma correction and nosie removal.

<div class="img">
        {% include figure.html path="assets/img/kk_nn.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Neural Network Implementation
</div>

The network has been grouped into three parts consisting of two, two and three convolutional layers separated by max pool layers between them. The features obtained after the seventh convolutional layer have been flattened and densed into a 1000-dimensional layer. This layer is used by the sigmoid function for the binary classification. The number of strides on the convolutional layers have been set to two with additional padding to prevent loss in features. Relu activation function has been used for non-linearization of the feature vector and helps in faster learning as it can easily back propagate the errors and have a constant gradient. Max pooling layers have been used to reduce the spatial size of the feature vector. In doing so the max pooling layers reduce the number of parameters and reduce the computational time and space of the following layers.

<div class="img">
        {% include figure.html path="assets/img/kk_graph.png" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Accuracy over time at different training sensitivities
</div>

<div class="img">
        {% include figure.html path="assets/img/kk_table.png" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Sensitivity and specificity values
</div>