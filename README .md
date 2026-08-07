# RNA-seq Differential Expression Analysis Pipeline using edgeR 

## Overview

This repository contains a reproducible and customizable RNA sequencing (RNA-seq) analysis pipeline for differential gene expression analysis using the edgeR package in R.

The workflow was developed to provide a transparent and easy-to-use framework for processing gene-level count data generated from RNA-seq experiments. The pipeline guides users from raw count files through quality control, differential expression analysis, visualization, and individual gene exploration.

Although the pipeline was originally developed for murine mammary gland RNA-seq data, it can readily be adapted for other organisms and experimental designs by modifying the user settings provided in each script.

The scripts are written to be generally applicable, allowing users to specify their own project directory, experimental groups, filtering thresholds, normalization settings, differential expression cut-offs, and visualization options.

The pipeline includes:

- Count matrix generation
- Quality control
- Filtering and normalization
- Differential expression analysis
- Volcano plot generation
- Individual gene visualization

## Workflow
```
Raw HTSeq count files
        │
        ▼
00_make_count_matrix.Rmd
        │
        ▼
01_data_QC.Rmd
        │
        ▼
02_DEG_analysis.Rmd
      │         │
      ▼         ▼
03_volcano_plot.Rmd
04_individual_gene_plot.Rmd 
```

## Repository structure

## Repository structure

```
RNAseq_edgeR_pipeline/
│
├── README.md
├── analysis_settings_manuscript.md
├── scripts/
│   ├── 00_make_count_matrix.Rmd
│   ├── 01_data_QC.Rmd
│   ├── 02_DEG_analysis.Rmd
│   ├── 03_volcano_plot.Rmd
│   └── 04_individual_gene_plot.Rmd
```

### Script descriptions

| Script | Purpose |
|---------|---------|
| **00_make_count_matrix.Rmd** | Combines individual HTSeq count files into a single count matrix. |
| **01_data_QC.Rmd** | Performs annotation, quality control, filtering and TMM normalization. |
| **02_DEG_analysis.Rmd** | Performs differential expression analysis using edgeR. |
| **03_volcano_plot.Rmd** | Generates publication-quality volcano plots and highlights genes of interest. |
| **04_individual_gene_plot.Rmd** | Creates violin plots for selected genes using normalized expression values. |

## Requirements

- R (≥4.3)

Main packages:

- edgeR
- DESeq2
- ggplot2
- enrichR
- clusterProfiler
- biomaRt
- org.Mm.eg.db 

## Running the analysis

## Running the pipeline

Run the scripts in the following order:

1. `00_make_count_matrix.Rmd`
2. `01_data_QC.Rmd`
3. `02_DEG_analysis.Rmd`
4. `03_volcano_plot.Rmd`
5. `04_individual_gene_plot.Rmd`

Each script contains a **USER SETTINGS** section where users can specify project-specific parameters such as directories, sample information, filtering thresholds, differential expression cut-offs and visualization settings.

## Input

HTSeq count files (.count)

Sample metadata

Mouse genome annotation

## Output

Count matrix

Quality control figures

Normalized expression values

Differential expression tables

Volcano plots

Individual gene plots


The parameter settings used for the accompanying manuscript are described in:

analysis_settings_manuscript.md
