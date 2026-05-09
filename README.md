# Hybrid ARO-ALO: Adaptive Metaheuristic Optimization for Histopathological Image Segmentation

## Overview
This repository contains the official Python source code and implementation details for the paper **Adaptive Hybrid ARO-ALO for Multi-Level Thresholding of Histopathological Colon Cancer Images**, in **The Visual Computer** (Springer). 

## Datasets
- Item Borkowski AA, Bui MM, Thomas LB, et al. Lung and Colon Cancer Histopathological Image Dataset (LC25000) 2019. https://doi.org/10.48550/ARXIV.1912.12142.
- Item Guan J, Guo J, Chen Q, et al. A High Magnifications Histopathology Image Dataset for Oral Squamous Cell Carcinoma Diagnosis and Prognosis. Sci Data 2026;13:371. https://doi.org/10.1038/s41597-026-06736-z.
- Item Sinitca AM, Lyanova AI, Kaplun DI, et al. Microscopy Image Dataset for Deep Learning-Based Quantitative Assessment of Pulmonary Vascular Changes. Sci Data 2024;11:635. https://doi.org/10.1038/s41597-024-03473-z.

The proposed methodology introduces a novel, unsupervised, multi-level image thresholding framework that synergistically combines **Artificial Rabbit Optimization (ARO)** and **Ant Lion Optimization (ALO)**. This hybrid architecture is specifically designed to segment high-resolution histopathological images (e.g., Colon Adenocarcinoma, Oral Squamous Cell Carcinoma, and Pulmonary Circulation Vessels) by preserving structural integrity, cellular morphology, and natural intensity gradients without requiring labeled ground-truth masks.

## Key Algorithms and Implementation Details
The core algorithm (`HybridARO_ALO`) addresses the premature convergence and local optima problems frequently encountered in high-level thresholding ($T \ge 10$). 

The optimization pipeline consists of two dynamic phases governed by an adaptive switching ratio (**$\lambda$**):
1. **Phase 1: Exploration via ARO:** The algorithm allocates the first fraction of iterations ($\lambda \times Epochs$) to the Artificial Rabbit Optimization model. This phase aggressively scans the global search space to locate the optimal multi-modal histogram valleys.
2. **Phase 2: Exploitation via ALO:** The remaining iterations are handed over to the Ant Lion Optimization model. ALO uses the best global solution found by ARO as its initial position and performs fine-grained exploitation to pinpoint the exact threshold boundaries.

**Objective Function:** The algorithm maximizes Otsu's Between-Class Variance to isolate cellular intensity clusters.

**Evaluation Metrics:** The script automatically calculates Peak Signal-to-Noise Ratio (PSNR), Structural Similarity Index (SSIM), Feature Similarity Index (FSIM), alongside Pearson and Spearman spatial correlation coefficients.

