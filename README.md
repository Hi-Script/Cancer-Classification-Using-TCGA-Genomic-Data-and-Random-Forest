Description
# Cancer Classification Using TCGA Genomic Data and Random Forest

## Overview
This project leverages genomic data from The Cancer Genome Atlas (TCGA) to classify patients as having cancer or being non-cancerous using a Random Forest classifier. The TCGA dataset contains ~1500 rows of copy number variation (CNV) data with columns like `patient_id` and `seg_mean` (log-ratio of copy number), while the label dataset includes 92 patients (46 cancer, 46 non-cancer), with 89 overlapping patient IDs. The pipeline aggregates CNV data into patient-level features, trains a Random Forest model, and evaluates performance using accuracy, precision, recall, F1-score, and AUC, with visualizations for interpretability.

This project addresses a real-world problem in precision oncology: predicting cancer status from genomic alterations, which can aid in early diagnosis or risk assessment. The current implementation achieves a cross-validation accuracy of ~0.686 and an AUC of ~0.86, with potential for improvement via feature engineering or model tuning.

## Features
- **Data Preprocessing**: Filters overlapping patient IDs and handles missing values.
- **Feature Engineering**: Aggregates `seg_mean` into patient-level statistics (mean, std, min, max, count).
- **Model**: Random Forest classifier with 100 trees, trained on stratified train-test splits.
- **Evaluation**: Computes accuracy, precision, recall, F1-score, and AUC, with a confusion matrix and feature importance visualizations.
- **Real-World Application**: Provides interpretable features for cancer diagnostics, with potential for clinical use.

## Dataset
- **TCGA Data** (`tcga_data.csv`): ~1500 rows with columns `patient_id`, `seg_mean`, and potentially others (e.g., `chrom`, `start`, `end`, `num_probes`).
- **Label Data** (`labels.csv`): 92 rows with columns `patient_id` and `label` (0 for non-cancer, 1 for cancer).
- **Overlap**: 89 patients are common between datasets, forming a balanced dataset (46 cancer, 46 non-cancer).

*Note*: The datasets are not included in this repository due to potential sensitivity. Users must provide their own TCGA and label data in CSV format.

## Requirements
- Python 3.8+
- Libraries: `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `seaborn`
- Install dependencies:
  ```bash
  pip install pandas numpy scikit-learn matplotlib seaborn
