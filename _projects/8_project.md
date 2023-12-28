---
layout: page
title: Bone MRI
description: Image processing for bone segmentation in MR Images
img: assets/img/mri_out.jpg
importance: 8
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
The main objective of this project is to segment, i.e. separate the bone from the tissues and other visible matter in the MRI (knee, brain, hip, etc). It should be agnostic to the body part in question and automatic, making the lives of doctors and hospitals easier by enabling them to better understand and to read MRIs. Using this MRIs can be used for scanning and testing our bones instead of an X-ray, thereby avoiding harmful effects of radiation on the patients. Designed a heuristic thresholding edge detection algorithm and an active contouring-based algorithm on MATLAB.
</p></div> 
<br>


<h4>De-noising</h4>
The use of histogram equalization for controlling contrast for effective thresholding is a main part of the de-noising and pre-processing. Because the backgrounds of MRI scans are so noisy and contain significant lighting artifacts, it is important to filter out the background before proceeding with other image processing techniques. Otherwise, the background compromises the effectiveness of these methods. Hence, filtering using a median filter to remove noise is a good method. Both have been implemented for an optimal result.

<h4>Sobel's Operation</h4>
This involves edge detection using Sobel masks. The Sobel operator is employed for conducting a 2-dimensional spatial gradient analysis on an image, accentuating areas with significant spatial frequency, which are indicative of edges. Its typical application involves estimating the absolute gradient magnitude at various locations within a grayscale image input. Then the image is thresholded at a value of 200 to binarize the image. Finally, a border-clearing function is applied to get rid of the boundary (the skin/surface of the MRI). This gives us the edges of the bones along with minor remnants from the tissues resulting in body-part-agnostic segmentation without machine learning applications.

<h4>Otsu's Operation</h4>
A simpler implementation for automatic segmentation might use adaptive Otsu thresholding. Otsu's thresholding technique entails a process of systematically examining all potential threshold values. It computes a dispersion metric for the pixel intensities on both sides of the threshold, representing the foreground and background. The objective is to identify the threshold value that minimizes the total spread of foreground and background pixel values. In theory, this would work well to separate the bright trabecular tissue or the dark cortical tissue of the bone from the other tissues. A fudge factor has been introduced which the user can input, the thresholding value will be using the factor accordingly.

In the various images below, there are four outputs which are respectively the original image, the noisy image, the output of method 1 (Sobel edge detection) and the output of method 2 (Otsu’s thresholding).

<div class="img">
        {% include figure.html path="assets/img/hip_out.PNG" title="Hip MRI" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Hip MRI
</div>

<div class="img">
        {% include figure.html path="assets/img/brain_out.PNG" title="Brain MRI" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Brain MRI
</div>

<div class="img">
        {% include figure.html path="assets/img/back_out.PNG" title="Back MRI" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Back MRI
</div>

<div class="img">
        {% include figure.html path="assets/img/knee_out.PNG" title="Knee MRI" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Knee MRI
</div>

<h4>Analysis</h4>
Both methods give decent results and segment the bones reasonably well. The issue with
Otsu’s thresholding is that in areas where the dark cortical tissue
is lighter, it gets labelled as a bright area, thus connecting the
bright trabecular and muscle tissues. Also, because the areas of
connection between bone and muscle tissue are so large at the
ends of the bones, they cannot be easily split with operations such
as morphological opening. The Sobel segmentation is cleaner than
adaptive Otsu segmentation, but like the Otsu method, Sobel
connects the bone tissue with muscle tissue at the ends of the
bones where the cortical layer is thin. The noise removal using the
median filter and also the contrast enhancement using histogram
equalisation work well for the given application. They deliver optimal results
without losing too much detail in the image. Also, in Sobel’s edge
detection there are fake and weak edges that create a lot of
confusion for the examiner to understand. 

<h4>Active Contouring</h4>
We also implemented Snakes also commonly known as active contouring. These are like flexible lines that adjust their shape to fit the edges of objects in images. They use both external forces to guide them and internal forces to resist changes in their shape. It is like a way to match a flexible model to an image by finding the best fit with the least energy.