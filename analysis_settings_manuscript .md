# Analysis settings used for the accompanying manuscript

This repository contains a general RNA-seq analysis pipeline with configurable user settings.

The analyses reported in the accompanying manuscript were performed using the following parameter settings.

## Data preprocessing

| Setting | Value used |
|---------|------------|
| Input data | HTSeq count files |
| Organism | Mouse (*Mus musculus*) |
| Genome | GRCm39 |
| Gene annotation | org.Mm.eg.db / biomaRt |

## Quality control

| Setting | Value used |
|---------|------------|
| Low-expression filter | >1 CPM |
| Minimum samples | 2 |
| Normalization | TMM |
| Dispersion estimation | edgeR estimateDisp() |

## Differential expression analysis

| Setting | Value used |
|---------|------------|
| Statistical package | edgeR |
| Model | Negative binomial GLM |
| Design | ~ Condition |
| Test | Likelihood ratio test (glmLRT) |
| Multiple testing correction | Benjamini–Hochberg |

## Differential expression thresholds

The pipeline allows users to specify their own thresholds.

For the accompanying manuscript the following thresholds were used:

| Purpose | Threshold |
|---------|-----------|
| Differential expression | |logFC| < 0.1 | FDR < 0.1 |
| Volcano plot | |logFC| > 0.1 | FDR < 0.1 |

## Functional enrichment

| Setting | Value used |
|---------|------------|
| Package | enrichR |
| GO database | GO Biological Process |
| Pathway database | Reactome |

## Visualization

Individual gene expression plots were generated using TMM-normalized logCPM expression values extracted from the edgeR object.

## Notes

The scripts in this repository are designed to be reusable for other RNA-seq datasets.

Researchers using this pipeline should modify the settings in the USER SETTINGS section of each script according to their own experimental design and analysis requirements. 
