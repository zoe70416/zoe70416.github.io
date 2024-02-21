---
layout: page
title: Network Intrusion Detection Systems Using Machine Learning
description: Buiding a network intrusion detection system (NIDS) using machine learning methods
img: assets/NIDS_hsrn.png
importance: 1
category: work
related_publications: true
---

<!-- Every project has a beautiful feature showcase page.
It's easy to include images in a flexible 3-column grid format.
Make your photos 1/3, 2/3, or full width.

To give your project a background in the portfolio page, just add the img tag to the front matter like so: -->


    ---
    layout: page
    title: project
    description: a project with a background image
    img: /assets/NIDS_hsrn.png
    ---

<!-- <div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/1.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/3.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Caption photos easily. On the left, a road goes through a tunnel. Middle, leaves artistically fall in a hipster photoshoot. Right, in another hipster photoshoot, a lumberjack grasps a handful of pine needles.
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div> -->
<!-- 
You can also put regular text between your rows of images, even citations {% cite einstein1950meaning %}.
Say you wanted to write a bit about your project before you posted the rest of the images.
You describe how you toiled, sweated, _bled_ for your project, and then... you reveal its glory in the next row of images.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>

The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above: -->
<!-- 
{% raw %}

```html
<div class="row justify-content-sm-center">
  <div class="col-sm-8 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
```

{% endraw %} -->


## Problem & Definition
Network Intrusion Detection poses a challenge as it can be framed either as a binary classification task (benign vs. malicious) or a multi-class classification task (DoS vs. DDoS, etc.). Given the difficulty in obtaining labels for real datasets and the current lack of necessity for identifying different attack types in HSRN, we categorize this problem as an unsupervised binary classification case.


## Hypothesis 
The architecture that proves effective for the example dataset will also demonstrate efficacy for our real dataset.

## Research Questions and Methods: 
1. How do deep autoencoding-based models compare to alternative paradigms for detecting network traffic anomalies?\\

We explored various ML methods (Algorithms: IF, AE, VAE, KitNET) based on unsupervised methods on similar simulated datasets (using zeek conn.log dataset) like IOT-23 and UNSW.


2. Does using aggregated statistics of network traffic as input features enhance model performance?\\
Our motivation for studying network flow aggregation arises from the potential to reveal new patterns beneficial for detecting network anomalies. We performed experiments to optimize our feature space by including eight aggregation features in dimensions such as the number of unique destination IPs, max bytes, average packets, etc. However, due to dataset limitations, we could only perform these over a window of 60 seconds and with the same source IP to ensure sufficient data.


3. What is the best way to deploy the NIDS in our real-world setting (HSRN lab)?

The optimal model that performs the best on the simulated dataset will be employed. We will also consider the systemd structure for deployment. \\
We believe that the adoption of systemd for deploying the NIDS can bring benefits in terms of service management, resource control, logging, and overall system efficiency.

## Results 

1. Alrogithms Experiments and Feature Aggregation: 
We conclude that VAE and KitNET are complex enough for the current feature space, and we should expand features for improvement. The incorporation of aggregation features improves most models, but KitNET, which achieved the highest F1, does not benefit from them. \\


Comparison of F1 scores among the best-performing AE-based architectures:\\ 
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/NIDS_AEbased_results.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Results for AE-based methods
</div>

2. Deployment: 

For efficient model deployment on HSRN, we opt for KitNET due to its performance and stability among the AE-based methods. Historical conn.logs are individually parsed and transformed to the feature space. Since HSRN is not open to public, we assume that all network flows are normal, utilizing which we estimate a KitNET. We deploy the most optimal configuration during the research. For inference, we develop scripts that input network logs to the trained KitNET model and output an anomaly score. Both training and inference processes are automated using Systemd, a Linux system, and a service manager. 

## In Progress: 

1. Deployment optimization
2. Deep Learning-Based Dynamic Bandwidth Allocation


## Links 
1. [Poster](https://drive.google.com/file/d/1WT5W0ozxse7-8da0I9eg3pDUbS8Rend7/view?usp=sharing) 
2. [Report](https://drive.google.com/file/d/1zZKCZvjy5QBvQM6_LUrxKyitkKV5IlJL/view?usp=sharing)
3. [Website](https://vip.hsrn.nyu.edu/)

