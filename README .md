# RNA-seq Differential Expression Analysis Pipeline using edgeR 

The pipeline includes:

- Count matrix generation
- Quality control
- Filtering and normalization
- Differential expression analysis
- Volcano plot generation
- Individual gene visualization

## Workflow

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

## Repository structure

scripts/

00_make_count_matrix.Rmd

Imports individual HTSeq count files and combines them into a single count matrix.

01_data_QC.Rmd

Performs gene annotation, filtering, TMM normalization and quality control.

02_DEG_analysis.Rmd

Performs differential expression analysis using edgeR.

03_volcano_plot.Rmd

Creates publication-quality volcano plots.

04_individual_gene_plot.Rmd

Plots expression of selected genes using TMM-normalized logCPM values.

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

Run the scripts in the following order:

1. 00_make_count_matrix.Rmd

2. 01_data_QC.Rmd

3. 02_DEG_analysis.Rmd

4. 03_volcano_plot.Rmd

5. 04_individual_gene_plot.Rmd

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
