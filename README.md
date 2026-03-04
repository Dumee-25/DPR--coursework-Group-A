# Treatment Response Prediction: DS202.3 Coursework (Group A)

## Project Overview
[cite_start]This project investigates whether routinely collected demographic and clinical variables can explain variations in treatment response patterns for cancer patients[cite: 5]. [cite_start]Since direct treatment response labels were unavailable in the dataset, this analysis focuses on constructing a **Response Proxy**—a composite score derived from multiple clinical outcomes—to predict patient success[cite: 6].

**Authors:** RKG Tharishika, KADP Kumarapeli  
**Date:** 2025-02-13  
[cite_start]**Course:** DS202.3 - Treatment Response Prediction [cite: 1, 2]

---

## 📂 Dataset
* [cite_start]**File Name:** `msk_chord_2024_clinical_data.tsv` [cite: 17]
* [cite_start]**Dimensions:** 25,040 Rows × 53 Columns [cite: 24, 27]
* **Context:** Real-world clinical oncology data including tumor sites, cancer types, genomic data, and survival statistics.

## 🛠 Dependencies
[cite_start]The analysis is performed in R using the following libraries [cite: 11-15]:
* `tidyverse` (Data manipulation and visualization)
* `gridExtra` (Plot arrangement)
* `corrplot` (Correlation matrices)
* `ggpubr` (Publication-ready plots)
* `knitr` (Report generation)
* `lubridate` (Date handling)
* `scales` (Graphical scaling)

## 📊 Methodology

### 1. Data Quality Assessment
* Conducted a comprehensive analysis of missing values.
* [cite_start]Variables with >50% missing data (e.g., Gleason Scores, PD-L1 status) were identified and largely excluded from the primary proxy construction[cite: 105, 111].
* [cite_start]Data filtering retained 98% of the original dataset (N=24,550)[cite: 1118].

### 2. Feature Engineering
[cite_start]We engineered 13 new features to support the analysis, including[cite: 1164]:
* [cite_start]**`stage_binary`**: Grouping patients into "Early" vs. "Advanced" stages[cite: 1124].
* [cite_start]**`disease_extent`**: Extracted from clinical notes (Localized, Regional, Distant)[cite: 1125].
* [cite_start]**`age_group`**: Categorized as Under 50, 50-65, and Over 65[cite: 1141].
* [cite_start]**`cancer_simple`**: Simplified grouping of major cancer types (Breast, Lung, Colorectal, Prostate, Pancreatic)[cite: 1145].

### 3. Response Proxy Construction
[cite_start]A 5-component composite score (scaled 0-100) was created to act as the target variable for "Treatment Response" [cite: 1167-1173]:
1.  **Survival Duration (Weight: 4)**: Based on survival quartiles.
2.  **Survival Status (Weight: 2)**: Alive vs. Deceased.
3.  **Disease Extent (Weight: 3)**: Localized vs. Distant spread.
4.  **Metastasis Presence (Weight: 2)**: Binary indicator.
5.  **Sample Type (Weight: 1)**: Primary vs. Metastatic sample.

## 🔑 Key Findings

### Strong Predictors
* **Disease Stage**: The most powerful differentiator. [cite_start]Early-stage patients had a mean response score of **70.3**, compared to **39.6** for advanced-stage patients[cite: 1785].
* **Cancer Type**: Significant variation exists. [cite_start]Prostate cancer showed the best response (Mean: 64.7), while Pancreatic cancer showed the worst (Mean: 46.3)[cite: 1892].
* [cite_start]**Metastasis**: Patients without metastasis had a mean response of **72.1**, vs. **32.0** for those with metastasis[cite: 1851].

### Moderate/Weak Predictors
* **Demographics**: Age and Sex showed weaker associations compared to clinical factors. [cite_start]Females had a slightly higher mean response (59.2) than males (56.9) [cite: 1752][cite_start], and younger patients (<50) performed slightly better than older groups[cite: 1724].

## 📈 Visualizations
The notebook includes detailed visualizations such as:
* [cite_start]Correlation matrices of component scores[cite: 1967].
* [cite_start]Boxplots comparing Response Index by Stage, Cancer Type, and Age[cite: 1755, 1854].
* [cite_start]Scatter plots with trend lines showing the relationship between Age/Survival and Response Index[cite: 1919].

## 🚀 Future Work
* Integration of genomic features (TMB, Fraction Genome Altered) into the prediction model.
* Temporal analysis to capture changes in treatment response over time.
