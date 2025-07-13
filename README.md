# Transcriptomic Profiling of Congenital Hyperinsulinism Beta Cells – Day 9 and Day 16

This repository contains curated R scripts and output files developed for an MSc research project at King’s College London. The project investigates transcriptomic changes in insulin-producing beta cells derived from induced pluripotent stem cells (iPSCs), focusing on congenital hyperinsulinism (CHI) caused by ABCC8 mutations. The repository is designed for reproducibility, modular reuse, and output integration with external functional analysis tools.

---

## Project Overview

Congenital hyperinsulinism (CHI) is a rare genetic condition characterised by inappropriate insulin secretion, often resulting from inactivating mutations in the ABCC8 gene. This study uses a CRISPR-based in vitro disease model derived from human iPSCs to analyse transcriptional profiles at two critical differentiation timepoints:

- **Day 9 (D9)**: Endocrine progenitor stage
- **Day 16 (D16)**: Insulin-expressing beta-like stage

Comparative transcriptomic analysis was performed between wild-type and CRISPR-edited (ABCC8-deficient) conditions to elucidate the molecular underpinnings of CHI. The pipeline integrates differential expression analysis, enrichment analysis (GO, KEGG, Reactome, GSEA), and heatmap visualisation of key gene sets.

---

## Repository Structure

The repository follows a modular structure to separate raw data, code, visual output, and downstream result tables.

.
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

This repository relies on both R and Python environments. All required packages are listed below or in the `environment.yml` file.

### R Packages

Install these CRAN and Bioconductor packages before running the R scripts:

```r
install.packages(c("dplyr", "tidyr", "tibble", "stringr", "ggplot2"))
BiocManager::install(c(
  "clusterProfiler", "org.Hs.eg.db", "enrichplot", 
  "biomaRt", "ComplexHeatmap", "circlize"
))
```
---

Python Environment
The Conda environment used for upstream pre-processing and optional exploratory analysis (e.g. pyDESeq2, GOATOOLS) is defined in environment.yml.

To create and activate the environment, run this in bash:

conda env create -f environment.yml
conda activate chi_pipeline

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

## Pipeline structure

Each script (d9_analysis.R and d16_analysis.R) follows this workflow:

1. Input loading
  - Normalised count matrix
  - Differential expression results (DEG)
  - Complete gene expression list (for ranking)
2. Preprocessing
  - Log-transformation of count matrix
  - Row and column reformatting for heatmap compatibility
3. Gene ID harmonisation
  - Map Ensembl IDs to HGNC symbols and Entrez IDs using biomaRt
4. Enrichment analysis
  - GO, KEGG, and Reactome overrepresentation tests
  - GSEA using MSigDB pathways (Hallmark, KEGG, Reactome)
5. Heatmap plotting
  - Identify top enriched pathways
  - Extract core enrichment genes from GSEA
  - Subset DEG–GSEA overlap for each top term
  - Z-score normalise and visualise via ComplexHeatmap
6. Export outputs
  - Save all enrichment results as CSVs in docs/d9/ and docs/d16/
  - Export gene lists for DAVID and PANTHER in respective folders

---

## Citation
If you use this repository or adapt the pipeline, please cite the MSc research project:

> Saldanha, A. (2025). *Transcriptomic profiling of insulin-expressing beta cells from congenital hyperinsulinism pancreas and induced pluripotent stem cells*. MSc in Applied Bioinformatics, King’s College London.


