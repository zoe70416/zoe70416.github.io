---
layout: page
title: Chest Radiology Report Generation
description: 
img: assets/img/chestxray.jpg 
redirect: 
importance: 4
category: fun
---

## Purpose 
This project aims to develop a generalizable chest X-ray report generation model by leveraging transfer learning from state-of-the-art multimodal approaches. Our model will integrate visual features from chest X-rays with structured pathology findings from Chexpert. By adapting to diverse datasets, this approach has the potential to enhance diagnostic capabilities and improve healthcare efficiency.

## Background & Motivation
Medical imaging serves as a cornerstone in modern diagnostics, with X-rays playing a piv- otal role due to their affordability and widespread availability in hospitals worldwide. They are particularly invaluable in analyzing lung conditions, aiding in the diagnosis and moni- toring of diseases such as pneumonia, pneumothorax, atelectasis, and edema (Johnson et al. (2019)). However, the sheer volume of chest X-rays requiring examination in daily clinical practice poses a significant challenge, compounded by a shortage of trained radiologists in many healthcare systems (Rosenkrantz AB and Jr (2016)). Consequently, automatic radiology report generation has emerged as a promising avenue of research to alleviate radiologists’ workload.

## Hypothesis 
Building upon Chantal’s pioneering work (Pellegrini et al. (2023)), this study adopts the BLIP-2 (Bootstrapping Language-Image Pre-training with Frozen Image Encoders and Large Language Models) architecture to integrate image features and structured pathol- ogy findings with a Large Language Model (LLM) (Li et al. (2023)). While the previous study utilized the MIMIC dataset for training, this work further refines the model perfor- mance by fine-tuning with LoRA and transferring learning to the Indiana University Chest X-ray dataset.

This study assumed a high degree of similarity between the image feature and image-text spaces of the MIMIC and IU chest X-ray datasets. This assumption allowed us to explore fine-tuning the model on the IU dataset.

## Dataset 
This study utilizes two publicly available chest X-ray datasets: MIMIC-CXR and IU X-ray.


## Model Architecture 
The model is consist of three parts: 

1. This component extracts both text-aligned image features and structured findings (the presence of 14 pathology classes, such as opacity, pneumonia, edema, etc.). For both types of features, the BioViL-T Image Encoder, a pre-trained domain-specific X-ray encoder, is used.

- An alignment module (Q-former) is further trained to obtain text-aligned image features.
- A CheXpert Classifier model is trained based on image features extracted by the BioViL-T Image Encoder to derive structured findings.

2. Prompt Construction:  This module converts image features, structured findings, and instructions into a single prompt, which serves as input for the LLM.

3. Language Model: Utilizing vicuna - 7b, an LLM, this model processes the con- structed prompt and generates context-specific responses, completing the radiology report generation process. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/chestxray_model.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Model Architecture 
</div>

## Methods
Both the alignment model and the LLM underwent further training/fine-tuning using the IU dataset.
1. Alignment Model: We fine-tuned the alignment model with visual language training on IU X-ray image-report pairs

2.  LLM Fine-tuning with LoRA: LoRA, or Low-Rank Adaptation, optimizes large mod- els by freezing pre-trained weights and introducing trainable rank decomposition matrices into each Transformer layer. This approach significantly reduces the number of trainable parameters for downstream tasks.

3. Prompt Engineering: In addition to the basic prompt utilized in the prior study, three additional prompts were developed to target distinct aspects of the report generation pro- cess, potentially enhancing report quality:
- Focus on Specific Findings
- Focus on Chest X-ray Analysis - Focus on Radiology Style


## Evaluation Metric 
To assess our model’s performance, we employed Natural Language Generation (NLG) metrics:
1. BLEU (Bilingual Evaluation Understudy): This metric, ranging from zero to one, gauges the similarity between machine-translated text and a set of high-quality reference translations.
2. METEOR (Metric for Evaluation of Translation with Explicit ORdering): METEOR compares the translated text to human reference translations by segmenting them into chunks and computing similarity using measures such as unigram precision, recall, F-score, bigram overlap, and exact word matches.
3. ROUGE (Recall-Oriented Understudy for Gisting Evaluation): ROUGE focuses on recall, determining how much information present in reference text(s) is captured by the generated text.


## Results
While our fine-tuned model achieved positive results on the IU dataset, the baseline model outperformed it on most evaluation metrics for chest X-ray reports. However, our model showed promise with the ”Focus on Specific Findings” prompt, achieving a higher METEOR score.

## Link
[Report](https://github.com/zoe70416/chest-xray-report-generation/blob/master/Deep_Learning_in_Medicine_Final_Paper_wh2405.pdf)
[GitHub](https://github.com/zoe70416/chest-xray-report-generation)