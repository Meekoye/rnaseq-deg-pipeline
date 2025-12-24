# rnaseq-deg-pipeline
This repository contains a complete RNA-seq differential gene expression analysis pipeline using TPM normalization. It compares sensitive and resistant sample groups, calculates log2 fold changes, performs statistical testing with FDR correction, identifies significantly up- and down-regulated genes, and visualizes results using a volcano plot.
# RNA-Seq Differential Gene Expression Analysis

A complete RNA-seq differential gene expression analysis pipeline using **TPM normalization**. This project compares **sensitive** and **resistant** sample groups, identifies **differentially expressed genes (DEGs)**, and visualizes results using a **volcano plot**.

---

## Overview

This repository implements a step-by-step RNA-seq analysis workflow that:

- Normalizes raw read counts using TPM  
- Computes log2 fold change between conditions  
- Performs statistical hypothesis testing  
- Applies false discovery rate (FDR) correction  
- Classifies genes as upregulated or downregulated  
- Visualizes results with a volcano plot  

---

## Input Data Format

The input file must be a CSV containing the following columns:

| Column Name | Description |
|------------|-------------|
| `Gene_ID` | Unique gene identifier |
| `Gene_Length (BP)` | Gene length in base pairs |
| `P001_sen`–`P005_sen` | Sensitive sample read counts |
| `P006_res`–`P010_res` | Resistant sample read counts |

---

## Dependencies

The pipeline requires the following Python libraries:

```bash
pip install pandas numpy scipy statsmodels matplotlib seaborn
Note: This analysis is designed to run in Google Colab and uses google.colab.files for file upload.
How to Run

Open the script or notebook in Google Colab

Upload the CSV file when prompted

Run all cells sequentially

Review printed results and the volcano plot
Analysis Workflow
1. Data Loading

Upload CSV file

Read gene counts into a DataFrame

2. TPM Normalization

Convert gene length from base pairs to kilobases

Compute Reads Per Kilobase (RPK)

Scale to Transcripts Per Million (TPM)

3. Differential Expression

Calculate mean TPM per condition

Compute log2 fold change

Perform Welch’s t-test

4. Multiple Testing Correction

Apply Benjamini–Hochberg FDR correction

5. Gene Classification

Label genes as Up, Down, or No Regulation

6. Visualization

Generate a volcano plot
DEG Thresholds
Metric	Cutoff
Log2 Fold Change	≥ 1 or ≤ −1
Adjusted p-value (FDR)	< 0.05
Volcano Plot Interpretation

X-axis: Log2 Fold Change

Y-axis: −log10(adjusted p-value)

Red dashed lines: Statistical and fold-change cutoffs

Significant DEGs appear in the upper left and right regions of the plot.
Output

The pipeline produces:

TPM-normalized expression values

DEG table containing:

Gene_ID

log2_fc

padj

−log10(padj)

Regulation status

Volcano plot visualization

Lists of top upregulated and downregulated genes
