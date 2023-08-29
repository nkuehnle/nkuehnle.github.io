---
title: "Transcriptomic Analysis of KSHV Infection"
excerpt: "I performed bulk and single-cell transcriptomic analyses of KSHV infected lymphatic endothelial cells, which are the best available <i>de novo</i> infection for modeling Kaposi's sarcoma. The results of this analysis are still largely confidential due to the competitive nature of this topic right now. A publication is in preparation pending some molecular imaging and mechanistic follow-up studies based on these results. Click above for a short discussion on some of the challenges this dataset presented and some of the methods employed to overcome them.<br><img src'https://nkuehnle.github.io/images/gallery/scRNA_Viral_Gene_Expression_Dotplot.png' height='75%' width='75%'><img src'https://nkuehnle.github.io/images/gallery/scRNA_Gene_Detection_Density.png' height='75%' width='75%'>"
collection: portfolio
permalink: rpg_nlp
---

# Overview
I performed bulk and single-cell transcriptomic analyses of KSHV infected lymphatic endothelial cells, which are the best available <i>de novo</i> infection for modeling Kaposi's sarcoma. The results of this analysis are still largely confidential due to the competitive nature of this topic right now. A publication is in preparation pending some molecular imaging and mechanistic follow-up studies based on these results.

# General Findings and Methods

## Bootstrapping of Pilot Samples to Estimate Model Performance
An issue biological researchers frequently ask regarding sequence-based analysis is how much data they "need." In the case of bulk RNA sequencing, decent estimates can be given based on the general task and genome involved assuming typical statistical inference methods (i.e. DESeq2). For single cell sequencing, where unsupervised machine learning models are one of the key models employed ("power calculations" do not exist for these models) and the diversity of a sample can be difficult to determine <i>a priori</i>, this presents a challenge. To maximize the possibility of novel discoveries while limiting overall cost, we performed a deep sequencing of the most cells we could feasible recover for infected and uninfected LEC of a single donor. We then evaluated performance (using the results of analysis given the full dataset) vs sequencing depth and number of cells collected by generating bootstrapped samples of fixed sizes. In the end, we found that we could reduce our overall costs per sample by 4-5X, chosing a safe margin we reduced cost on each sample by 2X and achieved a final savings of around 30% of the total experiment costs.

## QC Filtering and Viral Behaviors
One of the unique aspects of this dataset is the presence of KSHV infected samples. Notably, these samples present certain QC dilemmas as KSHV induced a host gene shutoff phenotype during its lytic replicative cycle. Thus, some of the methods typically used for filtering out dead cells or empty beads, such as the number of genes detected behave highly unusual. Thus we required slightly more complex filtering schemes to avoid removing populations of interest. Beyond this, we make use of simulation-based doublet filtering methods with a KNN classifier to remove many instances of probable doublets, ala Wolock, et al. Cell Systems (2019).

## Identifying Viral Infectious Stage
It is well-known that one of the biggest issues with single cell sequencing analyses is the sparsity of data and the systematic under-sampling of that data (leading to inflated zero values). Many single cell analyses involve so-called cell cycle scoring, using a set of 40-50 genes to characterize the cell cycle phase of a given cell. However, the KSHV genome is barely over 80 genes in total and some of these genes have unknown or controversial cell type specific expression or latent/lytic behavior. Thus, relying on similar sets of genes to identify viral infectious stage is problematic. We make use of advanved imputation methods to improve geneset scoring alongside a final assignment of viral stage based on clustering data. Through this we've not only been able to clearly identify the stage of viral infection cells are at, but identify certain (undisclosed) viral genes associated with viral latency (the primary stage associated with viral cancers).

![Viral Gene Clustering DGE](https://nkuehnle.github.io/images/gallery/scRNA_Viral_Gene_Expression_Dotplot.png)

![Viral Gene Clustering DGE](https://nkuehnle.github.io/images/gallery/scRNA_Gene_Detection_Density.png)

### And more!

# Access
Code will not be made available until pre-prints are available.

# Data Availability
Code will not be made available until pre-prints are available.
