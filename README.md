# Transcriptomic Profiling of Congenital Hyperinsulinism Beta Cells – Day 9 and Day 16

This repository contains curated R scripts developed for an MSc research project at King’s College London. The project investigates transcriptomic changes in insulin-producing beta cells derived from induced pluripotent stem cells (iPSCs), focusing on congenital hyperinsulinism (CHI) caused by the ABCC8 mutations. The repository is designed for reproducibility, modular reuse, and output integration with external functional analysis tools.

---

## Project Overview

Congenital hyperinsulinism (CHI) is a rare genetic condition characterised by inappropriate insulin secretion, often resulting from inactivating mutations in the ABCC8 gene. This study uses a CRISPR-based in vitro disease model derived from human iPSCs to analyse transcriptional profiles at two critical differentiation timepoints:

- **Day 9 (D9)**: Endocrine progenitor stage
- **Day 16 (D16)**: Islet-like organoids stagee

Comparative transcriptomic analysis was performed between wild-type and CRISPR-edited (ABCC8-deficient) conditions to elucidate the molecular underpinnings of CHI. The pipeline integrates differential expression analysis, enrichment analysis (GO, KEGG, Reactome, GSEA), and heatmap visualisation of key gene sets.

---

## Dependencies

This repository relies on both R and Python environments. Install the CRAN and Bioconductor packages before running the R scripts following the 'renv.lock' file, which contains a snapshot of all the dependencies and versions of the packages that were used in the R script. All required packages for the Python pipeline are covered in 'CHI_environment.yml' and some of the core R pacakges utilised in the script are listed below:

- **R Packages:**
  - `dplyr`
  - `biomaRt`
  - `ClusterProfiler`
  - `org.. Hs.eg.Db`
  - `tibble`
  - `enrichplot`
  - `ReactomePA`
  - `msgidbr`
  - `ComplexHeatmap`
  - `tidyverse`
  - `grid`
  - `Circlize`



---

## Key Features
- Timepoint-specific modular scripts for Day 9 and Day 16 RNA-seq comparisons
- Gene identifier harmonisation (Ensembl, HGNC, Entrez) to enable unified downstream enrichment analysis
- Differential gene expression processing, including filtering and annotation
- Gene set enrichment analysis (GSEA) using pre-ranked gene vectors
- Functional enrichment via GO, KEGG, and Reactome using clusterProfiler
- Automated mini-heatmap generation for DEG–GSEA overlapping core genes
- Condition-aware visualisation (CRISPR vs WT) for publication-quality figures
- External compatibility: Structured output of gene lists for DAVID and PANTHER analysis platforms

---

---

## Citation
If you use this repository or adapt the pipeline, please cite the MSc research project:

> Saldanha, A. (2025). *Transcriptomic profiling of insulin-expressing beta cells from congenital hyperinsulinism pancreas and induced pluripotent stem cells*. MSc in Applied Bioinformatics, King’s College London.


