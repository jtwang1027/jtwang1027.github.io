---
title: "RNA-seq visualization and analysis"
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




Example code can be found here.