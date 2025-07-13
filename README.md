# Transcriptomic Profiling of Congenital Hyperinsulinism Beta Cells – Day 9 and Day 16

This repository contains curated R scripts and associated outputs developed for an MSc research project exploring transcriptomic differences between wild-type and CRISPR-edited stem cell-derived beta cells in a model of congenital hyperinsulinism (CHI).

## 🎯 Project Overview

The project investigates transcriptional signatures at two critical differentiation stages:
- **Day 9**: Endocrine progenitors
- **Day 16**: Insulin-expressing beta-like cells

The scripts use differential gene expression (DGE), gene set enrichment analysis (GSEA), and targeted heatmap visualisation to compare wild-type and ABCC8-deficient (CRISPR) conditions to highlight disease-relevant molecular pathways.

## 🛠️ Key Features

- **ID Mapping**: Harmonises Ensembl, HGNC, and Entrez identifiers across datasets
- **DEG–GSEA Integration**: Highlights biologically meaningful overlaps between differentially expressed genes and enriched pathways
- **Heatmap Generation**: Automatically plots mini heatmaps of DEG–GSEA core genes using Z-score normalization
- **Condition-aware Visualisation**: Samples are labelled and ordered for direct WT vs CRISPR comparison
- **Modular Design**: Each script is self-contained and can be reused with alternative inputs

## 🗂️ Repository Structure

| Folder          | Contents                                                                 |
|------------------|--------------------------------------------------------------------------|
| `data/`          | Input data including normalized counts, DEG results, and gene lists for both timepoints |
| `scripts/`       | R scripts for Day 9 and Day 16 analysis pipelines                        |
| `figures/`       | All generated plots, with subfolders for `d9/`, `d16/`, and integrated comparisons |
| `docs/d9/`       | GO, KEGG, and GSEA result tables for Day 9                               |
| `docs/d16/`      | GO, KEGG, and GSEA result tables for Day 16                              |
| `LICENSE`        | Open-source MIT license                                                  |
| `.gitignore`     | Standard ignore rules for R/RStudio projects                             |

```text
.
├── data/
│   ├── d9_normalized_counts.csv
│   ├── d9_DEG_results.csv
│   ├── d9_all_genes.csv
│   ├── d16_normalized_counts.csv
│   ├── d16_DEG_results.csv
│   ├── d16_all_genes.csv
│
├── scripts/
│   ├── d9_analysis.R
│   └── d16_analysis.R
│
├── figures/
│   ├── d9/
│   ├── d16/
│   └── integrated_comparisons.png
│
├── docs/
│   ├── d9/
│   │   ├── GO_enrichment.csv
│   │   ├── KEGG_enrichment.csv
│   │   └── GSEA_enrichment.csv
│   └── d16/
│       ├── GO_enrichment.csv
│       ├── KEGG_enrichment.csv
│       └── GSEA_enrichment.csv
│
├── LICENSE
├── .gitignore
└── README.md
