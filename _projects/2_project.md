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


## Model Architecture 

- Core Model: PredNet architecture, specialized in video frame prediction. 
- Layer Design: Hierarchical structure with multiple layers for different levels of abstraction. 
- Temporal Dynamics: Incorporation of ConvLSTM cells to handle sequential data. 
- Predictive Coding: Each layer aims to predict the next layer's activations, minimizing prediction error. 
- U-Net Integration: Enhanced with U-Net for semantic segmentation, utilizing masks in predictions. 

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
