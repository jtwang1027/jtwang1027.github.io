---
title: "scRNA Seq integration, cluster annotation, gene set analysis"
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

## Batch normalization for integrating 8 scRNA Seq datasets
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


## Cell type annotation using CellMarkers

CellMarker [(paper)](https://academic.oup.com/nar/article/47/D1/D721/5115823) is manually curated from over 100k papers, including >13k cell markers of 467 cell types spanning 158 tissues [(db link)](http://biocc.hrbmu.edu.cn/CellMarker/). This dataset can easily be downloaded and compared against the top markers from each cluster. Here, we used *Human cell markers* (Human_cell_markers.txt), which assigns single genes (and respective proteins) to a corresponding cell and tissue type. As another option, *Single cell markers* (Single_cell_markers.txt), is derived from scRNA seq data and assigns multiple markers per cell type.

Using the CellMarker database, clusters: 1, 5, 7, 9, 10 and 11 were characterized by cell labels such as "Cancer stem cell" and/or "mesenchymal progenitor cell". Interestingly, these cancer subpopulations are enriched with different combinations of markers, such as CD44, CXCR4, ICAM1, CD24, MCAM, ABCG2, FLT1/VEGFR1. 

![cancer_markers_dotplot](https://user-images.githubusercontent.com/46359281/88618644-9ea45480-d067-11ea-9d23-1677d4776e85.png)

How are these markers reflected in the literature? Indeed, CD44 is expressed at high levels on tumor cells at the periphery [(1)](https://www.hindawi.com/journals/sci/2018/5387041/). CD24+ tumor cells are known to be highly proliferative, migratory and invasive [(2)](https://pubmed.ncbi.nlm.nih.gov/10446804/). And, CXCR4 is expressed in a subset of glioma cells with enhanced tumorgenicity[(3)](https://www.ingentaconnect.com/content/cog/or/2011/00000019/00000012/art00005). ABCG2 is a drug transporter that is overexpressed in glioma stem cells in comparison to astrocytes. Interestingly, increased ABCG2 expression reduced chemotherapy drug buildup, which suggests this subpopulation (cluster 10) may be more resistance to chemotherapy [(4)](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5522142/https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5522142/). Cluster 10 was also enriched for FLT1/VEGFR1 and PECAM1 expression, suggesting this subpopulation is of angiogenic nature [(5)](https://www.sciencedirect.com/science/article/pii/S1535610806000560https://www.sciencedirect.com/science/article/pii/S1535610806000560).


## Gene set enrichment analysis using AUCell
As another approach, we tested for gene set enrichment (using the Gene Ontology annotation) using [AUCell](https://www.bioconductor.org/packages/release/bioc/html/AUCell.html). In AUCell, gene expression rankings are built for each cell. Next, enrichment of each gene set is plotted against each cell's gene expression ranking (the top 5% of expressed genes). The calculated AUC indicates the proportion of genes in a gene set that are highly expressed (for a given cell).

![AUCell_gene_sets](https://user-images.githubusercontent.com/46359281/88752981-24d49f80-d129-11ea-911f-b525cfb4fcba.png)

Interestingly, several gene sets of biological relevance were significantly enriched. Previous work has identified IL-8 in the glioblastoma secretome, where it stimulates pro-angiogenic signals and endothelial permeability[(6)](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3447807/). This is further supported by the enrichment of the blood vessel remodeling gene set. In  addition, we identified 2 immune populations: T cells and antigen presenting cells (likely microglia). Microglia are well-known drivers of brain tumor pathobiology and can make up 1/3 of the tumor[(7)](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7288606/) These results suggest that gene set enrichment can be used to identify aberrant pathways in tumor subpopulations, and can be used to study cell and pathway usage heterogeneity.




