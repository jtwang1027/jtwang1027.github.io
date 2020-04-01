---
title: "Batch normalization of scRNA Seq from multiple cancer donors"
date: 2020-03-31
tags: [scRNA-seq, Seurat, cancer, glioblastoma, ncbi, codeathon]
header:
  image: "/images/nasa-unsplash.jpg"
  caption: "Photo credit: NASA (unsplash.com)"
excerpt: ""
mathjax: "true"
---

 [repository link](https://github.com/NCBI-Codeathons/Diversifying-the-pipeline-for-identifying-bulk-RNA-seq-derived-biomarkers-of-cancer-risk-within-sing)

## Background and Objective
scRNA-Seq data was generated from 8 high-grade glioma tumor patients (Yuan et al., 2018) [paper](https://genomemedicine.biomedcentral.com/articles/10.1186/s13073-018-0567-9). In this study, datasets were explored separately, and the findings were pooled for a unified conclusion. Here, we will integrate the datasets, accounting for batch effects using mutual nearest neighbhors or Seurat's anchors-based MNN. Next, we will use information from the combined dataset to identify cell types and markers & differentially enriched gene sets (link new post). 

## Workflow
We will explore 2 workflows:
1. Mutual nearest neighbors from *Batchelor* package using *SingleCellExperiment* objects and workflow
2. Anchors from *Seurat*.


## Results from integrating 8 scRNA Seq datasets
__Uncorrected__  
![uncorrected-batch-umap](https://user-images.githubusercontent.com/46359281/78103558-3dbb8700-73bb-11ea-99ff-e6ade122613b.jpeg)

__MNN__  
![MNN-integrated-umap](https://user-images.githubusercontent.com/46359281/78103613-588dfb80-73bb-11ea-8b66-df7824595c8c.jpeg)

__Seurat__  
![seurat-integrated-umap](https://user-images.githubusercontent.com/46359281/78180679-1bfce700-7431-11ea-8557-75e01a235bc3.jpeg)





### Mutual nearest neighbors (Haghverdi, 2018)

### Seurat Anchors (Stuart,2019)

