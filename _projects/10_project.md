---
layout: page
title: MLR
description: Grade prediction and analysis using ML
img: assets/img/mlr.png
importance: 10
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
The aim of the project was to help predict the grades of students and in the process analyze various machine learning techniques for the task and classify the best performer. Also performed theorytical analyses on the results to finally reason out the cause for performance differences across techniques. This was my first attempt at machine learning and gave me a holistic understanding of conventional ML techniques.
</p></div> 
<br>


<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        <div class="img">
            {% include figure.html path="assets/img/mlr_heatmap.png" title="Correlation Matrix" class="img-fluid rounded z-depth-1" %}
        </div>
        <div class="caption">
            Heatmap of Correlation Values
        </div>
    </div>
</div>

Firstly the data was pre-processed and cleaned. Then a correlation analysis was performed to understand the effect of variables on each other, including the final grades. The heatmap of the correlation values is presented above.

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        <div class="img">
            {% include figure.html path="assets/img/mlr_scat.png" title="PCA Scatter Plot" class="img-fluid rounded z-depth-1" %}
        </div>
        <div class="caption">
            PCA Scatter Plot
        </div>
    </div>
</div>

<h4>Decision Tree</h4>
Decision tree was the first method used to predict the grades, but the grades were classified into distics categories and the analysis was performed. A decision tree was programmed on R and using the library ‘rpart’ we split the data into 75% training and 25% test data. We trained the tree using the data and we collected the test and training errors using the data sets we have split. We can evaluate performance using these. The same analysis was performed after applying PCA to the decision tree giving much better results.

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        <div class="img">
            {% include figure.html path="assets/img/mlr_tree.png" title="Decision Tree" class="img-fluid rounded z-depth-1" %}
        </div>
        <div class="caption">
            Decision Tree Implementation
        </div>
    </div>
</div>


<h4>Naive Bayes Classifier</h4>
Next, the naive bayes classifier was used. The dataset is divided into two parts, namely, feature matrix and the response vector. Feature matrix contains all the vectors of the dataset in which each vector has the value of dependent features. Response vector contains the value of class variable for each row of feature matrix. The probability densities were mapped and the predictions were made with and without applying PCA.

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        <div class="img">
            {% include figure.html path="assets/img/mlr_prob.png" title="Probability Densities" class="img-fluid rounded z-depth-1" %}
        </div>
        <div class="caption">
            Probability Densities for the Features
        </div>
    </div>
</div>


<h4>SVM</h4>
Support vector machines were also implemented with and without the application of PCA and the use of CNN's was evaluated for the purpose of grade prediction. Finally the methods were all compared using accuracies of the predicted grades..

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        <div class="img">
            {% include figure.html path="assets/img/mlr_Acc.png" title="Accuracies Compared" class="img-fluid rounded z-depth-1" %}
        </div>
        <div class="caption">
            Accuracies of Different Techniques
        </div>
    </div>
</div>

