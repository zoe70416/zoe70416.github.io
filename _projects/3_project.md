---
layout: page
title: Differentiation Model for Insomnia Disorder 
description: a project that redirects to another website
img: assets/img/OSA.png
redirect: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8774350/ 
importance: 3
category: work
---


## Motivation

Obstructive sleep apnea (OSA) and insomnia often co-occur, creating diagnostic complexities. Research reveals insomnia prevalence in OSA patients ranging from 18% to 42%, with regional variations, such as 9.3% in US and Hong Kong adolescents, reflecting cultural influences. Ethnic disparities contribute to varying OSA rates, with higher prevalence observed in Asians and Hispanic/Mexican Americans.\\
OSA disrupts airflow during sleep, impacting arousal and sleep stages. Diverse OSA phenotypes arise from variations in arousal thresholds (ArTH). Shared symptoms between Insomnia Disorder (ID) and OSA complicate accurate diagnosis. Inappropriate treatments, like hypnotics, can exacerbate OSA, and tailoring interventions becomes intricate with differing disease severities, especially for low-ArTH OSA patients.\\
Despite being the gold standard, polysomnography (PSG) has limitations: the first-night effect, space constraints, and high costs. Extended waiting times for lab-PSG exacerbate the challenges. Low-cost alternatives, including questionnaires (ISI, PSQI, ESS), lack specificity. Existing methods, such as lab-PSG, home sleep tests (HST), and questionnaires, struggle to precisely classify OSA phenotypes and ID, prompting a need for innovative solutions.\\
Machine learning (ML) emerges as a promising avenue for accurate sleep disorder classification, with demonstrated success in medical applications. However, established models for ID and OSA phenotypes are currently lacking, underscoring the necessity for novel, easily obtainable predictors.\\

## Exploratory Data Analysis
All statistical analyses in this research were conducted using SPSS Version 18.0 (IBM, Chicago, IL, USA) and Python. The Shapiro–Wilk test was first used to examine the normality of the obtained continuous variables. Because the data of each variable were not normally distributed (Shapiro–Wilk test: p < 0.05), the Kruskal–Wallis H test was applied to examine the differences in parameters among the three groups. Dunn’s test was also employed to provide a pairwise comparison of the three groups(Insomnia Disorder (ID), low-ArTH OSA, and high-ArTH OSA ). The level of significance for all statistical analyses was set as 0.05.



## Model Architecture 

This study proposes utilizing simple features like body profiles (BMI, age, sex) and oximetry parameters to develop classification models for low-ArTH OSA, high-ArTH OSA, and ID. Applying logistic regression, kNN, naive Bayes, random forest, and SVM, our objective is to differentiate ID and OSA phenotypes accurately. Sleep parameter comparisons aim to delineate distinctive patterns across sleep disorder groups.

</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/diagnostics-12-00050-g002.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Schematic workflow
</div>

In terms of the input features, two types of datasets were employed in the training stage, namely, the oximetry-based model (type 1: oximetry parameters only) and combined model (type2: oximetry and body profile parameters).

</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/OSA_modelprocess.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Model establishment process
</div>

## Evaluation
The confusion matrices were computed from the testing data predicted using the selected model. These matrices indicated the values of true-positive, true-negative, false-positive, and false-negative results, which were used to determine performance in relation to accuracy, precision, recall, F1-score, and the area under the receiver operating characteristic curve. In regard to feature importance, only the models that demonstrated the highest accuracy in the oximetry and combined models were further investigated for their input feature contribution to prediction. 


## Results
Two types of models (oximetry and combined models) were established based on the machine learning approaches of LR, kNN, NB, RF, and SVM. First, in terms of the oximetry models, the overall accuracy ranged from 77.04% to 79.57%, with the RF model exhibiting the highest value compared with those of the other approaches. Similarly, with respect to the combined models, RF also outperformed the other five approaches in relation to accuracy (80.6%). Therefore, this study adopted the RF models as the selected models to classify the testing set and investigate the feature importance of both model types.

</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/OSA_Classificationresults.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Classification results of the testing set using the selected models (random forest, RF). Confusion matrices indicating the accuracy of the multiclass classification using the selected model (RF). (A) The prediction results based on the participants’ oximetry-related parameters (oximetry model); (B) The outcomes of the classification model with the anthropometric and oximetry-related parameters (combined model).
</div>


## Conclusion and Discussion
**Conclusion and Discussion:**

In the pursuit of developing models to distinguish between obstructive sleep apnea (OSA) phenotypes and insomnia disorder (ID) using readily available parameters, this study curated a dataset comprising 1579 Taiwanese patients exhibiting insomnia patterns. Two model types were devised: one exclusively leveraging oximetry parameters and another incorporating both oximetry and anthropometric parameters. These models were implemented through five machine learning approaches (LR, kNN, NB, RF, and SVM), with Random Forest (RF) emerging as the most accurate across both model types.\\

While no conclusive evidence supports the superiority of RF over alternative machine learning approaches, the observed outcomes can be partially attributed to RF's utilization of bagging and bootstrapping methods. These techniques mitigate classification fluctuations, expediting convergence during the training phase.\\

Several limitations warrant consideration for future research endeavors. Primarily, the dataset's confinement to a single ethnicity (Taiwanese population) and the exclusive focus on anthropometric parameters, rather than craniofacial features, underscore the need for broader inclusivity, especially given the influence of craniofacial factors on OSA symptoms in Asian populations.\\

Addressing model refinement is another critical aspect for future investigations. Incorporating a more comprehensive set of input features may enhance model accuracy. However, the retrospective nature of this study precluded the acquisition of certain factors associated with ID and OSA. Notably, interviews for questionnaire completion, including ISI, PSQI, and ESS, were omitted, and clinical symptom descriptions in medical records lacked uniformity, limiting the study's exploration of subjective variables like self-reported snoring levels, breathing pause frequencies, and other pertinent symptoms. Despite these limitations, the inclusion of such clinical responses could furnish valuable numeric features for the robust classification of ID and OSA.\\


[Paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8774350/)