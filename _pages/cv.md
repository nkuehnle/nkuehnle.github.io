---
layout: archive
title: "CV/Resume"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

[PDF copy here](https://nkuehnle.github.io/files/Neil_Kuehnle_Resume.pdf) (due to limited space some material is not included in the PDF copy)

Education
======
**PhD.** in Biomedical Science, **Northwestern University** (2023)<br>
**BSc.** in Molecular Biology, **Loyola University Chicago** (2014)
* **Certificates:** Management for Scientists and Engineers from Northwestern University Kellogg School of Management
* **Select Coursework:** Bioinformatics, Quantitative Biology, Biostatistics I/II (Statistical Survey/Regression Analysis), Mathematical Statistics I/II (Probability Theory/Statistical Inference), Machine Learning, Information Management for Data Science (SQL/database management)
* **Bootcamps:** Programming Concepts & Fundamentals, R Programming, R Tidyverse, Python Programming, Data Wrangling and Visualization in Python

Skills
======
*	Python: NumPy, Pandas, Scikit-learn, PyTorch, SciPy,  Statsmodels, Matplotlib, Biopython, RPy2 (R API for Python programing language), Dash/Plotly, and more
*	Other Languages: R (Tidyverse suite of pakcages, ggplot2, DESeq2 and other specific bioinformatics libraries), SQL (SQLite), Unix/Linux shell scripting (bash)
*	Tools/Miscellaneous: Git, GitHub actions, AWS (S3 cloud storage), Slurm, NextFlow/NF-Core, Tableau, Excel

Experience
======
**Northwestern University, Department of Microbiology-Immunology** (Chicago, IL)<br>
**Graduate Research Assistant** (January 2017 – Present)
* Studied the role of KSHV in HIV-associated cancers using both sequence and non-sequence based high-throughput technologies, such as genome-wide CRISPR screening, bulk and single-cell RNA (scRNA) sequencing, and automated drug screening
* Served as the primary data scientist in support of 3 grants, including on the largest single-cell genomics study conducted at Northwestern University to-date

**Loyola University Chicago, Department of Bioinformatics** (Chicago, IL)<br>
**Research Assistant** (May 2010 – Aug 2015)
*	Studied the microbial diversity of the Chicago’s Lake Michigan using targeted (bacterial 16S rRNA) and (viral genome) shotgun sequencing approaches
*	Developed a ChIP-based assay for assessing histone modifications of aberrantly expressed tandem repeat sequences in human cancers


Projects
======

## Dissertation: The Role of FLICE-Inhibitory Proteins in Primary Effusion Lymphoma ([Access](https://nkuehnle.github.io/role_of_flips_in_pel))
*	Identified novel regulators of ligand-independent, TRAIL-R1-mediated cell death and cFLIP dependence in KSHV-associated lymphoma using genome-wide synthetic CRISPR rescue screens
*	Published in the prestigious Cell Death & Differentiation & selected as a monthly reader’s choice paper 

## Transcriptomic Analysis of KSHV Infection (Private Repo)
*	Deployed multiple supervised (KNN, linear regression) and unsupervised (deep count autoencoder, PCA, UMAP, and Leiden clustering) machine learning techniques alongside traditional statistical inference methods (Chi-square, NB-GLM, and Kolmogorov-Smirnov) on single cell data for QA, cleaning, and hypothesis formation & testing
*	Estimated sample sizes necessary for stable algorithm performance via bootstrapping of single-cell pilot experiment samples, leading to a 33% reduction in research expenditures
*	Developed a fast Cython-based tool for analysis of miRNA/k-mer enrichment in bulk RNA samples (rolling hash algorithm + hypergeometric testing)


## Natural Language Processing on RPG Content ([Repo](https://github.com/nkuehnle/rpg_nlp))
*	Scraped and cleaned 3K+ pieces of fan-generated RPG content scraped from Reddit
*	Predicted multiclass labels using both TF-IFD bag of words (one-vs-rest SVM/SVC) and sequence based (RoBERTA- based transformer), achieving a macro- F1 score of .88 and AUC of .99

## Predicting Used Car Value ([Repo](https://github.com/nkuehnle/kmax_car_value_regression))
*	Imputed values for extensively incomplete dataset using single-variable, iterative methods
*	Performed ordinal (random forest) regression on the dataset to predict vehicle value on a heavily obfuscated and incomplete dataset, achieved an R2 of 0.91 and concordance index of 0.95

## PiPy-AWC ([Repo](https://github.com/nkuehnle/pipyawc))
* Automated water level controller for home aquaria using a Raspberry Pi
*	I developed this in part to practice software design patterns like factories, observer/callback, etc.

Publications
======
  <ul>{% for post in site.publications %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
