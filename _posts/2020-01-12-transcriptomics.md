---
title: "RNA-seq visualization and analysis in R"
date: 2019-12-25
tags: [data visualization, rna-seq, transcriptomics, heatmap]
header:
  image: "/images/dream_challenge.png"
#excerpt: "a"
mathjax: "true"
---

# *Generating heatmaps*
Starting from the expression matrix (ie output from DESeq2 or EdgeR):

1. Select genes to show: (for example using FC and pvalue cutoff or lfcShrink cutoff)

2. Z-scaling each gene

3. Calling heatmap.2 



# *Generating Volcano plots using EnhancedVolcano*

Source code [(link)](https://github.com/jtwang1027/RNA_Seq/blob/master/volcano_plots-rna-seq.md)

![volcano-plot](https://user-images.githubusercontent.com/46359281/74269596-b7969480-4cd7-11ea-9185-31b58d334bdf.png)


