# Transcriptomic Profiling of Congenital Hyperinsulinism Beta Cells – Day 9 and Day 16

This repository contains curated R scripts and output resources for an MSc research project at King’s College London. The project investigates transcriptomic differences in insulin-producing beta cells derived from induced pluripotent stem cells (iPSCs), specifically focusing on congenital hyperinsulinism (CHI) caused by ABCC8 mutations. The repository is designed for reproducibility, downstream analysis, and modular reuse.

---

## Project Overview

Congenital hyperinsulinism (CHI) is a rare genetic condition characterised by excessive insulin secretion and hypoglycaemia, often linked to inactivating mutations in genes such as ABCC8. This project uses CRISPR-modified and wild-type iPSC-derived pancreatic cells to model CHI in vitro. RNA sequencing data were analysed at two key differentiation timepoints:

- **Day 9 (D9):** Endocrine progenitors  
- **Day 16 (D16):** Insulin-positive beta-like cells

Differential expression analysis, gene ontology (GO), pathway enrichment (KEGG, Reactome), and gene set enrichment analysis (GSEA) were performed to investigate molecular perturbations in CHI.

---

## Repository Structure

The repository is organised as follows to facilitate data traceability and workflow modularity:

├── data/
│ ├── d9_normalized_counts.csv
│ ├── d9_DEG_results.csv
│ ├── d9_all_genes.csv
│ ├── d16_normalized_counts.csv
│ ├── d16_DEG_results.csv
│ ├── d16_all_genes.csv
│
├── scripts/
│ ├── d9_analysis.R
│ └── d16_analysis.R
│
├── figures/
│ ├── d9/
│ ├── d16/
│ └── integrated_comparisons.png
│
├── docs/
│ ├── d9/
│ │ ├── GO_enrichment.csv
│ │ ├── KEGG_enrichment.csv
│ │ └── GSEA_enrichment.csv
│ ├── d16/
│ │ ├── GO_enrichment.csv
│ │ ├── KEGG_enrichment.csv
│ │ └── GSEA_enrichment.csv
│ ├── david/
│ │ ├── d9_gene_list.txt
│ │ ├── d16_gene_list.txt
│ └── panther/
│ ├── d9_gene_list.txt
│ ├── d16_gene_list.txt
│
├── environment.yml
├── LICENSE
├── .gitignore
└── README.md

---

## Dependencies

This repository relies on both **R** and **Python** environments for various stages of the pipeline.

### R Package Dependencies

These scripts require the following CRAN and Bioconductor packages:

- `dplyr`, `tidyr`, `tibble`, `stringr`, `ggplot2`
- `clusterProfiler`, `org.Hs.eg.db`, `enrichplot`, `biomaRt`
- `ComplexHeatmap`, `circlize`

Install using:

```r
install.packages(c("dplyr", "tidyr", "tibble", "stringr", "ggplot2"))
BiocManager::install(c("clusterProfiler", "org.Hs.eg.db", "enrichplot", "biomaRt", "ComplexHeatmap", "circlize"))

---

## Python Environment
The environment.yml file lists all dependencies used to run upstream processing or optional GSEA steps in Python (e.g. using pyDESeq2, GOATOOLS, or Jupyter notebooks for exploratory data handling).

Create the conda environment via:

conda env create -f environment.yml
conda activate chi_pipeline

---

## Key Features
- Modular scripts for Day 9 and Day 16 analysis, compatible with different datasets or updated inputs.
- Differential expression filtering, identifier mapping (Ensembl → HGNC → Entrez), and integrated annotation.
- Enrichment analysis via GO, KEGG, Reactome, and MSigDB Hallmark collections using clusterProfiler and GSEA.
- Automated mini-heatmap generation for DEG–GSEA overlapping genes with proper CRISPR vs WT visual comparison.
- Output-ready formatting for DAVID and PANTHER via structured gene list export.

---

## Pipeline
The general workflow followed in both d9_analysis.R and d16_analysis.R is as follows:
1. Input: Load normalized counts and annotated DEG results
2. Log transformation: Apply log1p to normalized expression data
3. Gene ID harmonisation: Map Ensembl IDs to HGNC symbols and Entrez IDs
4. Enrichment analyses:
  a) GO, KEGG, and Reactome enrichment (via enrichGO, enrichKEGG, enrichPathway)
  b) Gene Set Enrichment Analysis (GSEA) with custom ranking vectors
5. Output export: Save enrichment result tables to docs/
6. Mini heatmap plotting:
  a) Identify core enriched genes per GSEA pathway
  b) Subset expression matrix by DEG–GSEA overlap
  c) Perform row-wise Z-score normalization
  d) Plot condition-aware clustered heatmaps
7. External gene list preparation: Export ranked gene lists to docs/david/ and docs/panther/

---

## Citation
If you use or adapt this repository, please cite the following MSc research project:

Transcriptomic profiling of insulin-expressing beta cells from congenital hyperinsulinism pancreas and induced pluripotent stem cells – MSc Research Project, King’s College London, 2025.
