---
layout: page
title: Bone Segmentation
description: Image processing for bone segmentation in MR Images
img: assets/img/mri_out.jpg
importance: 6
category: fun
---

The main objective of this project is to segment, i.e. separate the bone from the tissues and other visible matter in the MRI, be it the MRI of the knee, brain, hip, etc. It should be agnostic to the body part in question and automatic, for making the lives of doctors and hospitals easier by enabling them to better understand and to read MRI’s. Using this MRI’s can be used for scanning and testing our bones instead of an X-ray which is harmful given the radiation the subject is exposed to.

Denoising: The use of histogram equalisation for controlling contrast for effective thresholding is a main part of the de-noising and pre-processing. Because the backgrounds of MRI scans are so noisy and contain significant lighting artifacts, it is important to filter out the background before proceeding with other image processing techniques. Otherwise, the background compromises the effectiveness of these methods. Hence, filtering using a median filter to remove noise is a good method. Both have been implemented for an optimal result.

Method 1: This involves edge detection using Sobel masks. The Sobel operator performs a 2-D spatial gradient measurement on an image and so emphasizes regions of high spatial frequency that correspond to edges. Typically it is used to find the approximate absolute gradient magnitude at each point in an input grayscale image. Then the image is thresholded at a value of 200 to binaries the image. Finally a border clearing function is applied to get rid of the boundary (the skin/surface of the MRI). This gives us the edges of the bones along with a little from the tissue as perfect segmentation without machine learning application is very difficult to implement.

Method 2: A simpler implementation for automatic segmentation might use adaptive Otsu thresholding. Otsu's thresholding method involves iterating through all the possible threshold values and calculating a measure of spread for the pixel levels each side of the threshold, i.e. the pixels that either fall in foreground or background. The aim is to find the threshold value where the sum of foreground and background spreads is at its minimum. In theory, this would work well to separate the bright trabecular tissue or the dark cortical tissue of the bone from the other tissues. A fudge factor has been introduced which can be inputted by the used, the thresholding value will be scaled by that amount if it isn’t satisfactory.

In the various images below, there are four outputs which are respectively the original image, the noisy image, the output of method 1 (Sobel edge detection) and the output of method 2 (Otsu’s thresholding).

<div class="img">
        {% include figure.html path="assets/img/knee_out.PNG" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Knee MRI
</div>

<div class="img">
        {% include figure.html path="assets/img/brain_out.PNG" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Brain MRI
</div>

<div class="img">
        {% include figure.html path="assets/img/back_out.PNG" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Back MRI
</div>

<div class="img">
        {% include figure.html path="assets/img/hip_out.PNG" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Hip MRI
</div>

We can clearly see that both the methods are giving us decent results and are able to segment the bones roughly. The issue with Otsu’s thresholding is that in areas where the dark cortical tissue is lighter, it gets labelled as a bright area, thus connecting the bright trabecular and muscle tissues. Also, because the areas of connection between bone and muscle tissue are so large at the ends of the bones, they cannot be easily split with operations such as morphological opening. The Sobel segmentation is cleaner than adaptive Otsu segmentation, but like the Otsu method, Sobel connects the bone tissue with muscle tissue at the ends of the bones where the cortical layer is thin. The noise removal using the median filter and also the contrast enhancement using histogram equalisation are working well. They are giving optimal results without losing too much detail in the image. Also, in Sobel’s edge detection there are fake and weak edges that create a lot of confusion for the person to understand. Using dilation and other morphological operations are also giving unreal and wrong outputs.

We also implemented Snakes or commonly known as active contouring. A snake is an energy minimizing, deformable spline influenced by constraint and image forces that pull it towards object contours and internal forces that resist deformation. Snakes may be understood as a technique of matching a deformable model to an image by means of energy minimization.
