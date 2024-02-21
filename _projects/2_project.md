---
layout: page
title: Video Prediction
description: Video Prediction Using Combined Model 
img: assets/img/CLEVR.jpeg
importance: 2
category: work
giscus_comments: false
---

## Background 
This is a final project done by my team members (Rod Aryan, Kat Inchoco) and I for a NYU Courant course "DS-GA 1008 Deep Learning" taught by Yann Lecun and Alfredo Canziani. 


## Dataset 
The dataset features synthetic videos with simple 3D shapes that interact with each other according to basic physics principles. Objects in videos have three shapes (cube, sphere, and cylinder), two materials (metal and rubber), and eight colors (gray, red, blue, green, brown, cyan, purple, and yellow). In each video, there is no identical objects, such that each combination of the three attributes uniquely identifies one object.
For unlabeled, training and validation set, you will have all 22 frames for each video. For hidden set you will only have the first 11 frames of each video.


## Task
The task on hidden set is to use the first 11 frames to generate the semantic segmentation mask of the last frame (the 22nd frame). The performance is eval- uated by calculate the IOU between the ground truth and the generated mask.


## About this study

This study explores the intersection of unsupervised learning and video frame
prediction by integrating advanced deep-learning architectures. We present a novel
method that combines the strengths of the PredNet architecture, rooted in predictive
coding principles from neuroscience, with the capabilities of U-Net, a model highly
effective in image segmentation tasks. Our approach harnesses PredNet’s ability
to predict future video frames and utilizes U-Net to create segmentation masks
for these predictions. This synergistic application provides a detailed analysis of
video content, capturing both spatial and temporal dimensions comprehensively.

    ---
    layout: page
    title: project
    description: a project with a background image
    img: /assets/img/CLEVR.jpeg
    ---

## Model Architecture 

- Core Model: PredNet architecture, specialized in video frame prediction. 
- Layer Design: Hierarchical structure with multiple layers for different levels of abstraction. 
- Temporal Dynamics: Incorporation of ConvLSTM cells to handle sequential data. 
- Predictive Coding: Each layer aims to predict the next layer's activations, minimizing prediction error. 
- U-Net Integration: Enhanced with U-Net for semantic segmentation, utilizing masks in predictions. 

</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/videopred_model.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Proposed Model Architecture
</div>


## Evaluation Metric 
Performance measured by Intersection Over Union (IOU) between predicted and ground truth masks. 


## Results
Our model achieved a performance score of 0.0192.
The change potentially reflects some difficulty in the model understanding the correct color in the predicted images. Specifically, in the images predicted by the model submitted to the final leaderboard, the frames look more brown. This could be due to it "averaging" all colors rather than distinguishing between them.

## Conclusion and Future Work

Our method leverages the predictive coding capabilities of PredNet for future video frame prediction and the segmentation efficiency of U-Net. The results demonstrated that this combination provides a comprehensive analysis of video content, capturing both spatial and temporal dimensions. However,challenges such as the overfitting tendency in PredNet and the need for optimal training cycles in U-Net were identified. Looking forward, we aim to refine our approach by incorporating strategies, particularly the recommendation of predicting on segmentation masks instead of raw frames. This strategy could address the issues observed in our model, such as the ’brown filter’ effect on our predicted images, by providing a more focused and relevant training target for the network.\\

Further research will also delve into enhancing the integration of PredNet and U-Net, ensuring that the combined strengths of both models are utilized more effectively. This may involve fine-tuning the interplay between the predictive and segmentation components of the system to better handle complex video sequences. Ultimately, our goal is to develop a more robust and versatile system for video frame prediction and segmentation, one that can adapt to diverse visual environments and offer more accurate and detailed insights into video content.

<!-- 
<div class="row">
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
</div>

You can also put regular text between your rows of images.
Say you wanted to write a little bit about your project before you posted the rest of the images.
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
Here's the code for the last row of images above:

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
