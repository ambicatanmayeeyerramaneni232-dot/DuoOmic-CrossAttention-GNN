# Duo-Omic Cross-Attention Graph Neural Network (GNN) for Non-Invasive Cholangiocarcinoma Detection

Official repository for the research project submitted to the IRIS National Fair / ISEF (Computational Biology and Bioinformatics category).

## Overview
Cholangiocarcinoma (CCA) is an aggressive biliary tract malignancy characterized by late-stage diagnosis and poor survival rates. Standard diagnostic workflows rely on invasive tissue biopsies or single-modality assays that fail to capture complex multi-omic alterations. 

This project introduces a **Duo-Omic Cross-Attention Graph Neural Network** that integrates transcriptomic (RNA-seq) and epigenomic (DNA Methylation) profiles accessed from the TCGA-CHOL cohort via UCSC Xena.

---

## Key Methodological Features
- **Graph Formulation ($G = (V, E)$):** Maps genomic features onto graph topologies via PyTorch Geometric (`torch_geometric`).
- **Intermediate Feature-Level Fusion:** Implements dual `GATv2Conv` layers combined with a custom **scaled dot-product cross-attention module**, where epigenomic methylation features ($Q$) dynamically contextualize transcriptomic gene expression ($K, V$).
- **Explainability & Biological Validation:** Couples model weights with **SHAP** (SHapley Additive exPlanations) to extract top predictive CpG probes, validated via the KEGG 2026 database for enrichment in the **Notch Signaling Pathway**.

---

## Results Summary
- **Test Accuracy:** 100.00%
- **ROC-AUC Score:** 1.0000
- **Top Biomarkers:** Isolated primary CpG promoter probes (e.g., associated with `CDH1`, `MUC1`, and `NOTCH1`) driving biliary lineage differentiation.

---

## Repository Structure
- `DuoOmic_GNN_Pipeline.ipynb`: The primary Google Colab notebook containing end-to-end data ingestion, preprocessing, variance filtering, PyTorch Geometric graph construction, training loops, evaluation metrics, SHAP calculations, and KEGG API validation.

## How to Run
1. Open the `.ipynb` file directly in **Google Colab**.
2. Ensure runtime has a GPU accelerator enabled (`Runtime > Change runtime type > T4 GPU`).
3. Run all cells sequentially to reproduce the data loading, training convergence, and test evaluations.
