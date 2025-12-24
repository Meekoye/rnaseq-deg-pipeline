# rnaseq-deg-pipeline
This repository contains a complete RNA-seq differential gene expression analysis pipeline using TPM normalization. It compares sensitive and resistant sample groups, calculates log2 fold changes, performs statistical testing with FDR correction, identifies significantly up- and down-regulated genes, and visualizes results using a volcano plot.
RNA-Seq Differential Gene Expression Analysis

A complete RNA-seq differential gene expression analysis pipeline using TPM normalization. This project compares sensitive and resistant sample groups, identifies differentially expressed genes (DEGs), and visualizes results using a volcano plot.

Overview

This repository implements a step-by-step RNA-seq analysis workflow that:

Normalizes raw read counts using TPM

Computes log2 fold change between conditions

Performs statistical hypothesis testing

Applies false discovery rate (FDR) correction

Classifies genes as upregulated or downregulated

Visualizes results with a volcano plot

Input Data Format

The input file must be a CSV containing the following information:

Gene_ID: unique gene identifier

Gene_Length (BP): gene length in base pairs

P001_sen to P005_sen: sensitive sample read counts

P006_res to P010_res: resistant sample read counts

Dependencies

The pipeline requires the following Python libraries:

pandas

numpy

scipy

statsmodels

matplotlib

seaborn

This analysis is designed to run in Google Colab and uses google.colab.files for file upload.

How to Run

Open the script or notebook in Google Colab

Upload the CSV file when prompted

Run all cells sequentially

Review printed results and the volcano plot

Analysis Workflow
Data Loading

Upload CSV file

Read gene counts into a DataFrame

TPM Normalization

Convert gene length from base pairs to kilobases

Compute Reads Per Kilobase (RPK)

Scale to Transcripts Per Million (TPM)

Differential Expression

Calculate mean TPM per condition

Compute log2 fold change

Perform Welch’s t-test

Multiple Testing Correction

Apply Benjamini–Hochberg FDR correction

Gene Classification

Label genes as Up, Down, or No Regulation

Visualization

Generate a volcano plot

DEG Thresholds

Log2 fold change ≥ 1 or ≤ −1

Adjusted p-value (FDR) < 0.05

Volcano Plot Interpretation

X-axis represents log2 fold change

Y-axis represents −log10 adjusted p-value

Significant DEGs appear in the upper left and right regions

Output

The pipeline produces:

TPM-normalized expression values

DEG table with gene ID, fold change, adjusted p-value, and regulation status

Volcano plot visualization

Lists of top upregulated and downregulated genes
