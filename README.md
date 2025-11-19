# Predicting Short-Form Video Virality  
### TikTok & YouTube Shorts — Data Wrangling Final Project (2025)

This project builds a **pre-upload virality prediction pipeline** for TikTok and YouTube Shorts.  
It takes you from **raw Kaggle data → cleaned labeled dataset → EDA → NLP/topic modeling → predictive modeling** using only *pre-upload* metadata.

The goal is to understand which factors — **titles, topics, categories, timing, creator tier, etc.** — influence a video’s likelihood of going viral.

---

# 🧠 Table of Contents
- [What Is This Project?](#what-is-this-project)
- [Why This Matters](#why-this-matters)
- [Dataset Source & Credits](#dataset-source--credits)
- [Folder-Wise Breakdown](#folder-wise-breakdown)
- [How to Install](#how-to-install)
- [How to Run the Project](#how-to-run-the-project)
- [Dependencies](#dependencies)
- [Contributing](#contributing)
- [License](#license)
- [Maintainers / Contact](#maintainers--contact)

---

# What Is This Project?

This repository analyzes **2025 short-form content trends** from TikTok and YouTube Shorts using the **YouTube Shorts and TikTok Trends 2025** Kaggle dataset.  
It includes:

- Python-based data cleaning & labeling  
- R-based exploratory data analysis (EDA)  
- BERTopic modeling & title text NLP (Python)  
- Title-length vs watch-time analysis (R)  
- Baseline virality prediction models (Python)

All modeling intentionally avoids post-upload metrics (likes, watch retention) to simulate a **true pre-upload prediction pipeline**.

---

# Why This Matters

Only ~2% of short-form videos become viral BASED on our virality threshold of 500,000 views. This project explores:

- Which topics, titles, or categories trend more often  
- Whether timing patterns influence virality  
- How metadata differs between viral and non-viral videos  
- Whether virality is predictable *before uploading*  

---

# Dataset Source & Credits

This project uses publicly available metadata.

### Dataset Source (Kaggle)  
**“YouTube Shorts and TikTok Trends 2025”**  
By **Tarek Masry**  
🔗 https://www.kaggle.com/datasets/tarekmasryo/youtube-shorts-and-tiktok-trends-2025  

We acknowledge the dataset creator for making this resource available.

---

# Folder-Wise Breakdown

```
DataWranglingFinalProject/
├─ PredictiveModelBasicWC/
├─ EDA/
├─ NLP_and_title_data_wrangling/
├─ youtube_shorts_tiktok_trends_2025_labeled.csv
├─ data_dictionary.xlsx
└─ README.md
```

---

## 1. PredictiveModelBasicWC/ (Python)

**Purpose:**  
Contains the original Kaggle dataset and all Python notebooks/scripts responsible for:

- Data cleaning  
- Virality labeling (≥ 500,000 views = viral)  
- Feature engineering  
- Addressing class imbalance (~2% viral content)  
- Baseline modeling:
  - Logistic Regression  
  - Random Forest  
  - Gradient Boosting  

**Run in:** ✔ Python / Jupyter Notebook

---

## 2. EDA/ (R)

### Files:
1. **QBS_181_Final_Proj_EDA.Rmd**  
2. **Bin_Analysis_EDA.Rmd**

### Overview  
This folder explores differences between **viral and non-viral** videos from the labeled dataset.

Included analyses:
- Genre and category distributions  
- Upload-hour behavior  
- Watch-time differences  
- Viral vs non-viral metadata comparisons  
- Additional exploratory notes on trends and metadata patterns  

Uses R packages:
- `dplyr`, `ggplot2`, `stringr`, `lubridate`, base R functions

---

### 2.1 QBS_181_Final_Proj_EDA.Rmd  

**Data Cleaning & Preprocessing**
- Loads the labeled dataset  
- Removes unused variables  
- Creates two groups:
  - Viral (`viral == 1`)  
  - Non-viral (`viral == 0`)  

**Analysis & Visualizations:**
1. **Genre Distribution (viral vs non-viral)**  
2. **Category Distribution Comparison**  
3. **Top viral-dominant genres & categories**  
4. **Upload timing trends (hour of day)**  
5. **Average watch time by day of week**  
6. **Multiple comparative bar charts & line graphs**

---

### 2.2 Bin_Analysis_EDA.Rmd  

**Purpose:**  
Performs statistical analysis of **average completion rate (avg_comp_rate)** across predefined dataset bins.

Includes:
- Computing avg_comp_rate per bin  
- Statistical tests (t-tests, ANOVA, or non-parametric where appropriate)  
- Visualizing significant bin-level completion differences  
- Identifying bins with significantly higher or lower completion behavior  

**Note:**  
This file does *not* perform topic analysis or keyword modeling.  
It strictly focuses on **completion-rate patterns and statistical significance.**

---

## 3. NLP_and_title_data_wrangling/

### 3.1 `topic_modeling_example.ipynb` (Python)
Complete **BERTopic** workflow for YouTube/TikTok title text.

**Functionality:**
- Title cleaning (`clean_text`)  
- Embedding generation  
- BERTopic training  
- Topic assignment  
- Topic probability extraction  
- Filtering low-quality topics  
- Building topic label structures  
- Identifying topics more common in viral videos  

**Visual Outputs Generated:**
- `topic_dendrogram_clean.png`  
- `topic_intertopic_viral.png`  
- `viral_topic_lift.png`  

**Exports:**
- `topic_keywords_2.csv` — full topic-word-weight mapping  

---

### 3.2 `hse_181_project.Rmd` (R)
Analysis of whether **title length** predicts **average watch time** for **Friday uploads**.

Includes:
- Scatterplot of title length vs avg watch time  
- LOESS smoothing for nonlinear patterns  
- Viral vs non-viral color distinctions  
- High-contrast theme  
- Output:
  - `friday_title_length_watchtime_600dpi.png`  

---

## 4. Root Files

- **`youtube_shorts_tiktok_trends_2025_labeled.csv`**  
  Final cleaned & labeled dataset used for all project components.

- **`data_dictionary.xlsx`**  
  Definitions of all included variables.

---

# How to Install

### Clone the repo
```bash
git clone https://github.com/yourusername/DataWranglingFinalProject.git
cd DataWranglingFinalProject
```

### Install R dependencies
```r
install.packages(c("tidyverse", "ggplot2", "dplyr", "stringr", "lubridate", "knitr", "rmarkdown"))
```

### Install Python dependencies
```bash
pip install pandas numpy scikit-learn matplotlib seaborn nltk umap-learn bertopic sentence-transformers imbalanced-learn
```

---

# How to Run the Project

### A. Clean & label dataset (Python)
```bash
# Open and run notebooks/scripts in:
PredictiveModelBasicWC/
```

### B. Run EDA (R)
```bash
# In RStudio or R:
EDA/QBS_181_Final_Proj_EDA.Rmd
EDA/Bin_Analysis_EDA.Rmd
```

### C. Run NLP + Topic Modeling
```bash
# Python:
NLP_and_title_data_wrangling/topic_modeling_example.ipynb

# R:
NLP_and_title_data_wrangling/hse_181_project.Rmd
```

### D. Run Predictive Modeling
```bash
# Python:
PredictiveModelBasicWC/
```

---

# Dependencies

## R Packages
- tidyverse  
- ggplot2  
- dplyr  
- readr  
- stringr  
- lubridate  
- knitr  
- rmarkdown  

## Python Packages
- pandas  
- numpy  
- scikit-learn  
- matplotlib  
- seaborn  
- nltk  
- umap-learn  
- bertopic  
- sentence-transformers  
- imbalanced-learn  

---

# Contributing

Contributions are welcome!  
1. Fork the repo  
2. Create a branch  
3. Submit a PR  

---

# License

This project is licensed under the **MIT License**.  
Dataset © Kaggle / Tarek Masry — see Kaggle terms for usage.

---

# Maintainers / Contact

Maintained by the **Data Wrangling Final Project Team (2025)**.  
For questions, please open an issue on GitHub.


