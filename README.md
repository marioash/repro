# README
# Acute Myeloid Leukemia Heatmap Analysis

A comprehensive RNA sequencing analysis pipeline for visualizing gene expression patterns in Acute Myeloid Leukemia (AML) samples using hierarchical clustering heatmaps.

### Overview

- Analyzes RNA sequencing data from 19 AML model mice samples
- Performs hierarchical clustering analysis
- Creates annotated heatmaps showing gene expression patterns
- Compares treatment responses across different mutations

### Dataset

- Source: Shih et al., 2017 study (PubMed ID: 28193779)
- Accession: SRP070849
- Pre-processing: Quantile normalized through refine.bio
- Contains: 19 AML model mice samples

### Requirements

```r
# Required packages
install.packages(c(
  "pheatmap",
  "magrittr",
  "readr",
  "dplyr",
  "tibble",
  "sessioninfo"
))
```

### Directory Structure

project_root/
├── data/
│   └── SRP070849/
│       ├── SRP070849.tsv      # Gene expression data
│       └── metadata_SRP070849.tsv  # Sample metadata
├── plots/
│   └── aml_heatmap.png      # Generated heatmap
└── results/
    └── top_90_var_genes.tsv # Filtered gene data### Analysis Pipeline

Data Import and Setup- Read gene expression matrix and metadata
- Ensure consistent sample ordering
- Set random seed for reproducibility

Gene Selection- Calculate variance for each gene
- Select genes in upper quartile of variance
- Save filtered genes to results folder

Heatmap Generation- Create hierarchical clustering heatmap
- Include annotations for mutations and treatments
- Scale values row-wise
- Custom color scheme: deepskyblue → black → yellow

### Key Features

1. **Mutation Analysis**  - IDH2 mutant samples
  - TET2 mutant samples
  - Wild-type controls


2. **Treatment Comparison**  - Vehicle control groups
  - AG-221 treatment (for IDH2 mutants)
  - 5-Azacytidine treatment (for TET2 mutants)


3. **Quality Control**  - Sample order validation
  - Variance-based gene filtering
  - Row-wise normalization



### Usage Instructions

Clone repository and navigate to project directoryInstall required packagesDownload dataset from refine.bio (SRP070849)Run the R Markdown notebookGenerated outputs will be saved in plots/ and results/ directories### Output Files

- `aml_heatmap.png`: Hierarchical clustering heatmap with annotations
- `top_90_var_genes.tsv`: Filtered gene expression data
- Session information log for reproducibility

### Citations

- Dataset: Shih et al., 2017 (PubMed ID: 28193779)
- Heatmap visualization: pheatmap package by Slowikowski et al., 2017
- Original analysis adapted from refine.bio-examples notebook

### Acknowledgments

This analysis was adapted from the CCDL for ALSF repository and modified for this repository by Candace Savonen.