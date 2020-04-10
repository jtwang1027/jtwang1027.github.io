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

### Bootstrapping / custom AMIs
In addition to the software listed above, additional software and packges are likely going to be needed. These can be installed while the cluster is being provisioned via boostrapping actions (which can be a series of bash scripts). As another option, you can select/create your own AMIs (Amazon machine images) from The AWS marketplace that already contains operating system & software you need--such as conda, rstudio, tensorflow 2+ and pytorch. But, running instances of these marketplace AMIs typically cost extra.

From  my own experience, the bootstrapping can add an unusually long amount of time. (Instead of a normal 5-7 min startup, bootstrapping can add 10-20min). While you're testing bootstrapping scripts, I would pay close attention to the logs that are being generated, and remember to supply -yes flags to proceed through installations when needed. If you're unsure the programs are being installed correctly, it's worthwhile to ssh into the master node and install the packages from the command line.

### Using spot instances to save on cost


<img width="260" alt="aws-cluster_setup-spot_inst" src="https://user-images.githubusercontent.com/46359281/78968180-f5dee300-7ad1-11ea-8da4-b2c732dd3c26.png">

## Background on IC50 prediction

MoleculeNet [(paper,](https://arxiv.org/abs/1703.00564)[website)](http://moleculenet.ai/) is a benchmark established by Vijay Pande's group at Stanford for molecular machine learning. MoleculeNet curates data from multiple public sources, such as ChEMBL, to establish 4 categories for molecular-based machine learning: quantum mechanics, physical chemistry, biophysics, and physiology. The benchmark showcases the performance of various types of models and chemical featurizations. Here, the BACE dataset will be used, which contains IC50 values for chemical inhibitors of human beta-secretase 1 (BACE-1).

## Featurization and ML in cheminformatics
Rdkit and deepchem are great packages for cheminformtaics and machine learning, and they incorporate functions for featurizing chemical data (such as using extended connectivity fingerprints)as well as generating machine learning models, including graph convolutional networks. Here, we explore an approach for representing molecules as vectors (mol2vec)[(paper)](https://pubs.acs.org/doi/abs/10.1021/acs.jcim.7b00616). Mol2vec is inspired by NLP techniques like word2vec, and learns vector representations of molecular substructures. Here,the pre-trained model was applied to the BACE dataset to see if it could improve IC50 prediction.

