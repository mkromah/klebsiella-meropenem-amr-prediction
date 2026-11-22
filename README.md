# klebsiella-meropenem-amr-prediction
Machine learning-based genomic prediction and SHAP interpretation of meropenem resistance in Klebsiella pneumoniae.

# 🧬 Machine Learning-Based Genomic Prediction and SHAP Interpretation of Meropenem Resistance in *Klebsiella pneumoniae*

### 🔍 Overview

In this project, I used machine learning to study meropenem resistance in *Klebsiella pneumoniae* using genomic resistance features. I used SHAP to examine which features contributed most to model predictions and plotted patterns across locations and years.

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
I trained a supervised model using genomic AMR features and used SHAP (SHapley Additive exPlanations) to interpret its predictions.

---

## ⚙️ Methods and Workflow

### 1️⃣ Data Acquisition and Cleaning

* Source: curated genomic AMR surveillance data for *K. pneumoniae* isolates.
* Key fields: `AMR_genotypes`, `Location`, `Year`, and isolate metadata.
* I cleaned and standardized location and gene entries.

### 2️⃣ Label Definition

* Resistance label defined by presence of key carbapenemase genes:
  `blaKPC`, `blaNDM`, `blaOXA`, `blaVIM`, `blaIMP`.

### 3️⃣ Feature Extraction

* I encoded AMR gene lists with **CountVectorizer** to make a binary gene-presence matrix.
* I encoded year and location as additional features.

### 4️⃣ Model Development

* **Algorithm:** Random Forest Classifier (200 estimators, balanced).
* **Validation:** 80/20 split + 5-fold cross-validation (mean F1 = 0.955 ± 0.007).
* **Performance:** Accuracy = 95.8 %; high sensitivity for resistant isolates (96.6 %).

### 5️⃣ Explainability and Interpretation

* I used **SHAP** to examine these top model features:
  `blaKPC-2`, `blaOXA-1`, `aac(6’)-Ib-cr5`, `parC_S80I`, `gyrA_S83I`.
* I generated summary bar plots, beeswarm plots, and isolate-level force plots.

### 6️⃣ Geospatial and Temporal Analysis

* I plotted the country-level distribution, including Tunisia, Brazil, and Pakistan.
* I plotted resistance trends using a three-year rolling mean.

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

* The model performed well on the dataset used here; we still need independent validation before assuming the same performance elsewhere.
* SHAP helped me see which recorded genomic features contributed most to predictions; it does not establish a causal gene–phenotype relationship.
* Recorded resistance patterns varied by country. Dataset sampling may contribute to those differences.

---

## 🧾 Citation

If you reuse this work, please credit:

> **Musa Al-Hassan Kromah** (2025). *Machine Learning-Based Genomic Prediction and SHAP Interpretation of Meropenem Resistance in Klebsiella pneumoniae.* Kaggle / GitHub Project.

---

## 🧪 Keywords

*Klebsiella pneumoniae* • Meropenem resistance • Machine learning • SHAP • Genomic prediction

---

## 🤝 Acknowledgements

* Wellcome Genome Campus – AMR 2026 Conference inspiration.
* NCBI and BV-BRC databases for genomic AMR data access.
* Kaggle computational environment for pipeline execution.
