---
title: "scRNA Seq integration and cluster annotation"
date: 2020-03-31
tags: [scRNA-seq, Seurat, cancer, glioblastoma, ncbi, codeathon]
header:
  image: "/images/nasa-unsplash.jpg"
  caption: "Photo credit: NASA (unsplash.com)"
excerpt: ""
mathjax: "true"
---

 [repository link](https://github.com/NCBI-Codeathons/Diversifying-the-pipeline-for-identifying-bulk-RNA-seq-derived-biomarkers-of-cancer-risk-within-sing/tree/master/batch_normalization)

## Background and Objective
scRNA-Seq data was generated from 8 high-grade glioma tumor patients (Yuan et al., 2018) [paper](https://genomemedicine.biomedcentral.com/articles/10.1186/s13073-018-0567-9). In this study, datasets were explored separately, and the findings were pooled for a unified conclusion. Here, we will integrate the datasets, accounting for batch effects using mutual nearest neighbhors or Seurat's anchors-based MNN. Next, we will use information from the combined dataset to identify cell types and markers & differentially enriched gene sets (see *Cluster Annotation* below).

## Batch normalization for integrating 8 scRNA Seq
We will explore 2 workflows:
1. Mutual nearest neighbors from *Batchelor* package using *SingleCellExperiment* objects and workflow [(code)](https://github.com/NCBI-Codeathons/Diversifying-the-pipeline-for-identifying-bulk-RNA-seq-derived-biomarkers-of-cancer-risk-within-sing/blob/master/batch_normalization/mnn-integration.rmd)
2. Anchors from *Seurat*.[(code)](https://github.com/NCBI-Codeathons/Diversifying-the-pipeline-for-identifying-bulk-RNA-seq-derived-biomarkers-of-cancer-risk-within-sing/blob/master/batch_normalization/seurat-integration.rmd)

### Results from integrating 8 scRNA Seq datasets
__Uncorrected__  
![uncorrected-batch-umap](https://user-images.githubusercontent.com/46359281/78103558-3dbb8700-73bb-11ea-99ff-e6ade122613b.jpeg)

__Mutual nearest neighbors (Haghverdi, 2018)__  
![MNN-integrated-umap](https://user-images.githubusercontent.com/46359281/78103613-588dfb80-73bb-11ea-8b66-df7824595c8c.jpeg)

__Seurat anchors (Stuart,2019)__  
![seurat-integrated-umap](https://user-images.githubusercontent.com/46359281/78180679-1bfce700-7431-11ea-8557-75e01a235bc3.jpeg)

## Clustering 


## Cell type annotation
We compared 3 approaches for cell type annotation: CellMarkers database, Panglao database, and using gene set enrichment. We found CellMarkers to be the most informative in this context.

### CellMarkers
CellMarker [(paper)](https://academic.oup.com/nar/article/47/D1/D721/5115823) is manually curated from over 100k papers, including >13k cell markers of 467 cell types spanning 158 tissues [(db link)](http://biocc.hrbmu.edu.cn/CellMarker/). This dataset can easily be downloaded and compared against the top markers from each cluster. Here, we used *Human cell markers* (Human_cell_markers.txt), which assigns single genes (and respective proteins) to a corresponding cell and tissue type. As another option, *Single cell markers* (Single_cell_markers.txt), is derived from scRNA seq data and assigns multiple markers per cell type.

Using the CellMarker database, clusters: 1, 5, 7, 9, 10 and 11 were characterized by cell labels such as "Cancer stem cell" and/or "mesenchymal progenitor cell". Interestingly, these cancer subpopulations are enriched with different combinations of markers, such as CD44, CXCR4, ICAM1, CD24, MCAM, ABCG2, FLT1/VEGFR1. 

![cancer_markers](https://user-images.githubusercontent.com/46359281/88617544-e4135280-d064-11ea-973b-50a3a3b57764.png)

How are these markers reflected in the literature? Indeed, CD44 is expressed at high levels on tumor cells at the periphery [(1)](https://www.hindawi.com/journals/sci/2018/5387041/). CD24+ tumor cells are known to highly proliferative, migratory and invasive [(2)](https://pubmed.ncbi.nlm.nih.gov/10446804/). And, CXCR4 is expressed in a subset of glioma cells with enhanced tumorgenicity[(3)](https://www.ingentaconnect.com/content/cog/or/2011/00000019/00000012/art00005). ABCG2 is a drug transporter that is overexpressed in glioma stem cells in comparisin to astrocytes. Interestingly, increased ABCG2 expression reduced chemotherapy drug buildup, which suggests this subpopulation (cluster 10) may be more resistance to chemotherapy [(4)](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5522142/https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5522142/). Cluster 10 was also enriched for FLT1/VEGFR1 and PECAM1 expression, suggesting this subpopulation is of angiogenic nature [(5)](https://www.sciencedirect.com/science/article/pii/S1535610806000560https://www.sciencedirect.com/science/article/pii/S1535610806000560).


### Gene set ORA (over-representation analysis)
As another approach, we tested for gene set enrichment with the expectation of finding significant biological processes that would be unique to a specific cell / tissue type. Using the Gene Ontology database and signifcant differentially expressed genes from each cluster, we applied *goana* for over-representation analysis. The results can be found in *enriched_gene_sets_by_cluster.rds*.

