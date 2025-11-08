# klebsiella-meropenem-amr-prediction
Machine learning-based genomic prediction and SHAP interpretation of meropenem resistance in Klebsiella pneumoniae.

# 🧬 Machine Learning-Based Genomic Prediction and SHAP Interpretation of Meropenem Resistance in *Klebsiella pneumoniae*

### 🔍 Overview

This repository presents a complete and explainable **machine learning pipeline** for predicting *meropenem resistance* in *Klebsiella pneumoniae* using genomic antimicrobial resistance (AMR) profiles.
The study integrates **bioinformatics**, **machine learning**, and **explainable AI (SHAP)** to identify the key genetic determinants associated with carbapenem resistance and to visualize their global and temporal distribution.

---

## 📂 Project Structure

```bash
klebsiella-pneumoniae-meropenem-amr-prediction/
│
├── data/
│   ├── kp_meropenem_ncbi.tsv
│   └── kp_amr_dataset.tsv
│
├── notebook/
│   └── klebsiella-pneumoniae-meropenem-amr-prediction.ipynb
│
├── results/
│   ├── shap_summary.png
│   ├── resistance_heatmap.png
│   ├── temporal_trend.png
│   ├── confusion_matrix.png
│   └── feature_importance.png
│
├── README.md
└── requirements.txt
```

---

## 🧠 Background

Carbapenem-resistant *Klebsiella pneumoniae* (CRKP) is a major global health concern.
Resistance is commonly driven by **carbapenemase genes** such as *blaKPC*, *blaNDM*, and *blaOXA*.
This project applies **supervised learning** to predict resistance phenotypes from genomic AMR data and employs **SHAP (SHapley Additive exPlanations)** for transparent model interpretation.

---

## ⚙️ Methods and Workflow

### 1️⃣ Data Acquisition and Cleaning

* Source: curated genomic AMR surveillance data for *K. pneumoniae* isolates.
* Key fields: `AMR_genotypes`, `Location`, `Year`, and isolate metadata.
* Cleaned and standardized location and gene entries.

### 2️⃣ Label Definition

* Resistance label defined by presence of key carbapenemase genes:
  `blaKPC`, `blaNDM`, `blaOXA`, `blaVIM`, `blaIMP`.

### 3️⃣ Feature Extraction

* Encoded AMR gene lists using **CountVectorizer** → binary gene presence matrix.
* Added metadata features (year, location) as categorical encodings.

### 4️⃣ Model Development

* **Algorithm:** Random Forest Classifier (200 estimators, balanced).
* **Validation:** 80/20 split + 5-fold cross-validation (mean F1 = 0.955 ± 0.007).
* **Performance:** Accuracy = 95.8 %; high sensitivity for resistant isolates (96.6 %).

### 5️⃣ Explainability and Interpretation

* **SHAP analysis** identified top genomic predictors:
  `blaKPC-2`, `blaOXA-1`, `aac(6’)-Ib-cr5`, `parC_S80I`, `gyrA_S83I`.
* Generated global bar and beeswarm plots + isolate-specific force plots.

### 6️⃣ Geospatial and Temporal Analysis

* Country-level heatmap showing resistance hotspots: Tunisia, Brazil, Pakistan.
* Smoothed (3-year rolling) resistance trend visualization over time.

---

## 📊 Results Summary

| Metric              |                                                              Value |
| ------------------- | -----------------------------------------------------------------: |
| Total isolates      |                                                              1,195 |
| Resistant isolates  |                                                         780 (65 %) |
| Accuracy            |                                                         **95.8 %** |
| Mean F1 (5-fold CV) |                                                  **0.955 ± 0.007** |
| Key predictors      | *blaKPC-2*, *blaOXA-1*, *aac(6’)-Ib-cr5*, *parC_S80I*, *gyrA_S83I* |
| Resistance hotspots |                                          Tunisia, Brazil, Pakistan |

---

## 🧩 Key Visualizations

* **Feature Importance Plot** – top 15 predictive genes
* **SHAP Summary Plot** – global feature impact
* **SHAP Force Plot** – per-isolate interpretability
* **Country Heatmap** – geographic resistance distribution
* **Temporal Trend** – rolling mean of resistance rates (global and by country)
* **Confusion Matrix** – model performance visualization

---

## 🧬 Technologies Used

| Category         | Tools / Libraries           |
| ---------------- | --------------------------- |
| Programming      | Python 3.10                 |
| Machine Learning | scikit-learn / RandomForest |
| Explainability   | SHAP                        |
| Visualization    | Matplotlib, Seaborn         |
| Data Handling    | Pandas, NumPy               |
| Environment      | Kaggle / Jupyter Notebook   |

---

## 📈 Key Findings

* Machine learning can accurately predict **meropenem resistance** from genomic features.
* Explainable AI (SHAP) reveals biologically meaningful gene–phenotype relationships.
* Resistance is geographically heterogeneous, highlighting **regional surveillance needs**.

---

## 🧾 Citation

If you use this repository or reproduce the workflow, please cite:

> **Musa Al-Hassan Kromah** (2025). *Machine Learning-Based Genomic Prediction and SHAP Interpretation of Meropenem Resistance in Klebsiella pneumoniae.* Kaggle / GitHub Project.

---

## 🧪 Keywords

*Klebsiella pneumoniae* • Meropenem resistance • Machine learning • SHAP • Genomic prediction

---

## 🤝 Acknowledgements

* Wellcome Genome Campus – AMR 2026 Conference inspiration.
* NCBI and BV-BRC databases for genomic AMR data access.
* Kaggle computational environment for pipeline execution.
