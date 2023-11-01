---
layout: page
title: DICOM
description: End to end DICOM viewer with an AI segmentation tool.
img: assets/img/dicom.JPG
importance: 3
category: fun
---

Developed a DICOM image viewer, browser and library which can support multiple imaging modalities (X-Ray, CT, PET, MR). Deployed it as a dockerised service. The patient browser allows users to upload dataset to browser, browse through exams stored in the database and displays essential details (Patient Name, Patient ID, Modality, Description, Date, Series Number, Series Description, Image Number, Location, Thickness, Spacing) of the exam. The browser allows seamless connectivity between patient exam and iteratively navigates through patient, exam, series, and image. The taskbar panel allows the user to select and launch various applications linked to the browser. Browser is designed to allow rapid integration with external applications.

<div class="img">
        {% include figure.html path="assets/img/dicom_flow.png" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Flow diagram for the viewer and library
</div>

<div class="img">
        {% include figure.html path="assets/img/dicom_deployment.png" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Deployment architecture
</div>

The image viewer is called from the browser when an image is launched. The viewer has functionality to scroll across slices in a single scan and allows the user to move across scans for a single patient. It has the feature to vary Window Level (Brightness) and Window Width (Contrast) of the image being displayed. Allows viewing of multiple series through multiple viewports in a single screen and displays relevant annotations (series name, image number, slice number, orientation, patient name, etc.) in the viewport. Users are allowed to set an upper and lower threshold for image pixel values and can also edit and insert new DICOM tags to the currently opened DICOM exam. Images can be re-oriented as sagittal/axial/coronal/oblique in the viewer. 

<div class="img">
        {% include figure.html path="assets/img/dicom_sequence.png" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Sequence website for the viewer and library
</div>

We additionally implemented authentication, user management and measures to preserve safety of the data being stored. Implemented a startup script and unit configuration file to automate startup of the service and configured reverse proxy for backend service. Allowed image deletion from the UI and added tools like Flood-Fill, LiveWire and Draw to the viewer. Added an extensive logging mechanism on the entire deployed service.

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        <div class="img">
            {% include figure.html path="assets/img/dicom_aiflow.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
        </div>
        <div class="caption">
            Flow diagram for the segmentation tool
        </div>
    </div>
</div>

We then designed an AI powered brain segmentation application that segments Gray Matter (GM), White Matter (WM), and Cerebrospinal Fluid (CSF) from the Neuro-MR exams. The brain segmentation application was deployed as an independent containerised service linked to the image viewer tool. The tool also helped visualise the three segmentations over the brain MR scan as an overlay. It could be customised to view different segmentations at a given time. For example, view only GM and CSF overlay, view only WM and GM overlay, and any such combination. The application allowed segmentation mask visualisation in planes other than the acquisition plane, an exam scanned and segmented in the axial plan could be viewed in the coronal/sagittal plan as well. 
There were around 700 patient exams with masks. Each segmentation mask corresponding to the exam had three labels, i.e., Gray Matter (GM), White Matter (WM), and Cerebrospinal Fluid (CSF). There were several exams which come from the same patient, rescanned on the same day. These very similar scans were biassing the model. Implemented robust data wrangling and pre-processing methods to identify and isolate such cases. The model training was done on an AWS EC2 ensuring optimised usage and cost. We used a U-NET based model for our application given how effective autoencoder-decoders are for semantic segmentation. For the pre-processing, we applied bias field correction to remove the low frequency noise in MRI’s and histogram equalisation for better normalisation of data being used. We also performed pixel normalisation and skull/scalp stripping. The Adam optimizer was used to train the model and the loss function used was sparse categorical cross entropy given its advantages in multi-class segmentation applications.

<div class="img">
        {% include figure.html path="assets/img/dicom_model.JPG" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    U-NET architecture used
</div>

Results of the segmentation model tested with a blind dataset of 80 images:
1. Dice Score: 0.87 (WM); 0.83 (GM); 0.65 (CSF)
2. Specificity: 0.99 (WM); 0.98 (GM); 0.99 (CSF)
3. Sensitivity: 0.87 (WM); 0.84 (GM); 0.63 (CSF)
4. Miss Rate: 0.12 (WM); 0.15 (GM); 0.36 (CSF)
5. False Positive Rate: 0.01 (WM); 0.01 (GM); 0.01 (CSF)
6. Positive Predictive Value: 0.87 (WM); 0.81 (GM); 0.69 (CSF)
7. Negative Predictive Value: 0.99 (WM); 0.99 (GM); 0.99 (CSF)

<div class="img">
        {% include figure.html path="assets/img/dicom_seg.png" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Segmentation results
</div>

UI design involved and the templates are confidential property of GE and cannot be shared publicly.
