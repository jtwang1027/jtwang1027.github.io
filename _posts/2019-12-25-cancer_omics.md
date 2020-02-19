---
title: "Multiomics analysis of cancer cell lines"
date: 2019-12-25
tags: [cancer, multiomics, proteomics, transcriptomics, genomics, single cell]
header:
  image: "/images/cancer_omics/dream_challenge.png"
#excerpt: "a"
mathjax: "true"
---

# *cancer omics*
DREAM challenge- Single cell signaling in breast cancer (genomics, transcriptomics, proteomics, phosphoproteomics) [(link)](https://www.synapse.org/#!Synapse:syn20366914/wiki/593925)



<img width="330" alt="screenshot" src="https://user-images.githubusercontent.com/46359281/71352057-4c380e00-2543-11ea-81a8-82add3663ece.png">

# *Biological motivation*


This challenge involves analysis of the largest single cell signaling dataset (67 cancer cell lines). The motivation is to understand the heterogenous, time-dependent responses to multiple drug treatments. In understanding single-cell and cancer line responses to treatments, we aim to predict responses to drug candidates.

![dream](https://user-images.githubusercontent.com/46359281/71548582-88190c00-2965-11ea-97fd-6dedbb1eeb4a.png)


[(link)](https://www.synapse.org/#!Synapse:syn20366914/wiki/593925)

This analysis will be broken down into:

1. Exploratory data analysis: Examining time-dependent drug responses and identifying similarities in cell lines. [(link)](https://github.com/jtwang1027/cancer_omics/blob/master/1_EDA_cell_line_exploration.ipynb)

2. Investigating feature importance in predicting phosphorylation changes in response to drug treatment using elastic net (ridge, LASSO) and tree-based models (random forests, xgboost) [(link)](https://github.com/jtwang1027/cancer_omics/blob/master/2A_elastic_net.ipynb)

3. Prediction using neural networks [(link)](https://github.com/jtwang1027/cancer_omics/blob/master/3_neural_network.ipynb)
<img src="../images/cancer_omics/tensorboard.png" alt="tensorboard" width="200"/>


4. Prediction using automl (tpot) with comparison to the above models. 
