---
title: "PySpark in AWS for predicting small molecule IC50"
date: 2020-04-10
tags: [distributed computing, AWS, pyspark, moleculenet, deepchem, rdkit,cloud computing,machine learning, EMR, molecule2vec]

header:
  image: "/images/nasa-unsplash.jpg"
  caption: "Photo credit: NASA (unsplash.com)"
excerpt: ""
mathjax: "true"
---

 [repository link](https://github.com/jtwang1027/pyspark_aws)



## Configuring AWS elastic MapReduce for distributed computing
AWS EMR
### Software options
<img width="639" alt="aws-cluster_setup-software" src="https://user-images.githubusercontent.com/46359281/78968102-dfd12280-7ad1-11ea-97b5-6f3d4e8bb542.png">

### Using spot instances to save on cost
<img width="260" alt="aws-cluster_setup-spot_inst" src="https://user-images.githubusercontent.com/46359281/78968180-f5dee300-7ad1-11ea-8da4-b2c732dd3c26.png">

### Bootstrapping / custom AMIs


## Background on IC50 prediction

MoleculeNet [(paper,](https://arxiv.org/abs/1703.00564)[website)](http://moleculenet.ai/) is a benchmark established by Vijay Pande's group at Stanford for molecular machine learning. MoleculeNet curates data from multiple public sources, such as ChEMBL, to establish 4 categories for molecular-based machine learning: quantum mechanics, physical chemistry, biophysics, and physiology. The benchmark showcases the performance of various types of models and chemical featurizations. Here, the BACE dataset will be used. The BACE datasets contains IC50 values for chemical inhibitors of human beta-secretase 1 (BACE-1).



