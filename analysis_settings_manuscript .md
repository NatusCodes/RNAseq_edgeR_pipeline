# Analysis settings used for the accompanying manuscript

This repository contains a general RNA-seq analysis pipeline with configurable user settings.

The analyses reported in the accompanying manuscript were performed using the following parameter settings.

## Data preprocessing

| Setting                        | Value used                   |
| ------------------------------ | ---------------------------- |
| Input data                     | HTSeq gene-level count files |
| Organism                       | Mouse (*Mus musculus*)       |
| Reference genome               | GRCm39                       |
| Gene annotation                | `org.Mm.eg.db`               |
| Ensembl-to-symbol mapping      | Enabled                      |
| Unmapped genes                 | Removed                      |
| Duplicate gene-symbol mappings | First occurrence retained    |

## Quality control and normalization

| Setting                     | Value used                                                    |
| --------------------------- | ------------------------------------------------------------- |
| Expression-filtering method | Manual CPM filtering                                          |
| CPM threshold               | >1 CPM                                                        |
| Minimum number of samples   | 2                                                             |
| Normalization               | TMM                                                           |
| Sample-level QC             | Library size, expression distributions, sample distances, PCA |

## Differential expression analysis

| Setting                     | Value used                                 |
| --------------------------- | ------------------------------------------ |
| Statistical package         | `edgeR`                                    |
| Model                       | Negative-binomial generalized linear model |
| Experimental predictor      | Condition (CTL/ELS)                        |
| Additional covariates       | None                                       |
| Test                        | Likelihood-ratio test (`glmLRT`)           |
| Multiple-testing correction | Benjamini–Hochberg                         |
| Comparison direction        | ELS − CTL                                  |

Positive log2FC values therefore indicate higher expression in ELS, whereas negative log2FC values indicate higher expression in CTL.

## Differential expression and volcano-plot thresholds

The statistical model was fitted for all genes retained after expression filtering. Differential-expression thresholds were applied after model fitting.

| Purpose                                  | Threshold used        |
| ---------------------------------------- | --------------------- |
| Gene-level interpretation / volcano plot | absolute log2FC > 0.1 |
| FDR threshold                            | <0.1                  |
| Multiple-testing correction              | Benjamini–Hochberg    |

Volcano plots were generated from the complete edgeR differential-expression result table rather than from a previously thresholded DEG subset.

## Individual gene visualization

Selected genes of interest were visualized using TMM-normalized logCPM expression values derived from the filtered edgeR object.

No additional hypothesis test or statistical cutoff was applied during generation of the individual gene plots. Gene selection was based on the preceding differential-expression analysis and biological interpretation.

## Gene Set Enrichment Analysis (GSEA)

GSEA was performed using the complete ranked list of tested genes rather than a DEG-filtered subset.

| Setting                                 | Value used                                    |
| --------------------------------------- | --------------------------------------------- |
| Package                                 | `clusterProfiler`                             |
| Gene-set analysis                       | GO GSEA                                       |
| Ontology                                | Biological Process (BP)                       |
| Gene identifier used for GSEA           | Entrez ID                                     |
| Ranking statistic                       | `-log10(raw P value) × sign(log2FC)`          |
| Ranking input                           | Complete differential-expression result table |
| GSEA multiple-testing correction        | Benjamini–Hochberg                            |
| Number of permutations                  | 10,000                                        |
| Enrichment interpretation               | Adjusted pathway P value / FDR                |
| Reported pathway significance threshold | adjusted P value <0.1                         |

The raw gene-level P value was used only to construct the ranked gene list. Biological interpretation of the GSEA results was based on the multiple-testing-adjusted pathway P values returned by the enrichment analysis.

## Functional overrepresentation analysis

Overrepresentation analysis was performed separately from GSEA.

| Setting                | Value used                   |
| ---------------------- | ---------------------------- |
| Package                | `enrichR`                    |
| GO database            | `GO_Biological_Process_2025` |
| Pathway database       | `Reactome_Pathways_2024`     |
| Significance threshold | adjusted P value <0.1        |

## Lipid-metabolism analysis

Genes involved in lipid/fatty-acid metabolism were identified by comparison with a predefined lipid-metabolism gene list derived from Jackson Laboratory/MGI resources.

Genes from this list were highlighted in the volcano-plot analysis when present in the RNA-seq differential-expression results.

## Notes

The scripts in this repository are designed to be reusable for other RNA-seq datasets.

Researchers applying the pipeline to other datasets should modify the settings in the **USER SETTINGS** section of each script according to their experimental design, organism, statistical thresholds, and visualization requirements.

