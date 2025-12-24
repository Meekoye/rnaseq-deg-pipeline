# rnaseq-deg-pipeline
This repository contains a complete RNA-seq differential gene expression analysis pipeline using TPM normalization. It compares sensitive and resistant sample groups, calculates log2 fold changes, performs statistical testing with FDR correction, identifies significantly up- and down-regulated genes, and visualizes results using a volcano plot.
# RNA-Seq Differential Gene Expression Analysis

This repository contains a Python-based RNA-seq differential gene expression analysis workflow. The script performs **TPM normalization**, compares **sensitive** and **resistant** sample groups, identifies **differentially expressed genes (DEGs)**, and visualizes results using a **volcano plot**.

---

## Overview

The analysis pipeline includes:

* Loading raw gene count data from a CSV file
* Normalizing expression values using TPM
* Calculating log2 fold change between conditions
* Performing statistical testing using Welch’s t-test
* Correcting p-values using Benjamini–Hochberg FDR
* Classifying genes as upregulated or downregulated
* Visualizing DEGs with a volcano plot

---

## Input Data Requirements

The input file must be a CSV file containing:

* `Gene_ID` — unique gene identifier
* `Gene_Length (BP)` — gene length in base pairs
* Count columns for each sample, for example:

  * `P001_sen`, `P002_sen`, `P003_sen`, `P004_sen`, `P005_sen`
  * `P006_res`, `P007_res`, `P008_res`, `P009_res`, `P010_res`

---

## Dependencies

The script requires the following Python libraries:

```bash
pip install pandas numpy scipy statsmodels matplotlib seaborn
```

This script is designed to run in **Google Colab** and uses `google.colab.files` for uploading input files.

---

## How to Run

1. Open the script in Google Colab
2. Upload the gene count CSV file when prompted
3. Run the script cells sequentially
4. Review printed DEG tables and the volcano plot

---

## Analysis Steps

1. **TPM Normalization**

   * Convert gene length to kilobases
   * Compute Reads Per Kilobase (RPK)
   * Scale values to Transcripts Per Million (TPM)

2. **Differential Expression**

   * Compute mean TPM per condition
   * Calculate log2 fold change
   * Perform Welch’s t-test per gene

3. **Multiple Testing Correction**

   * Apply Benjamini–Hochberg FDR correction

4. **Visualization**

   * Generate a volcano plot showing significant DEGs

---

## DEG Significance Criteria

* Log2 fold change ≥ 1 or ≤ −1
* Adjusted p-value (FDR) < 0.05

Genes meeting these thresholds are classified as **upregulated** or **downregulated**.

---

## Output

The script produces:

* TPM-normalized expression values
* A DEG results table containing:

  * Gene ID
  * Log2 fold change
  * Adjusted p-value
  * Regulation status
* A volcano plot visualization

---
