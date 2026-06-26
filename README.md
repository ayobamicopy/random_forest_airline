# ✈️ Airline Passenger Satisfaction Prediction & Optimization Engine

## 📌 Business Case & Project Overview
Manual prioritization of passenger complaints results in operational inefficiencies and declining retention rates for airline management. This project replaces reactive surveys with an optimized **Random Forest Ensemble Model** designed to systematically identify, predict, and rank passenger dissatisfaction vectors in real time. 

---

## 🛠️ Validation Split & Hyperparameter Optimization Rationale

### 1. Anti-Leakage Data Strategy (60/20/20 Split)
To completely insulate model selection from data leakage, the data asset was partitioned into three distinct sets:
* **Training Set (60%):** Outlines the base decision parameters for individual trees.
* **Validation Set (20%):** Used exclusively for structural tuning and hyperparameter selection.
* **Testing Set (20%):** Kept completely isolated as an unseen data layer for final evaluation.

### 2. Tuning via PredefinedSplit
Standard $K$-Fold cross-validation mixes data partitions, which can introduce evaluation bias. To maintain strict boundaries, we implemented `PredefinedSplit`. By passing an explicit index array flagging the precise training bounds (marked as `-1`) and validation bounds (marked as `0`), the hyperparameter search engine evaluated parameters solely against the designated validation partition.

* **Optimized Configurations Isolated:** `n_estimators: 100`, `max_depth: 15`, `min_samples_leaf: 2`.

---

## 📊 Performance Comparison Matrix

The ensemble model effectively resolves the high variance patterns found in the standard baseline Decision Tree:

| Performance Metric | Baseline Single Decision Tree | Optimized Random Forest Ensemble | Strategic Management Impact Gain |
|--------------------|-------------------------------|----------------------------------|----------------------------------|
| **Accuracy** | 88.42%                        | **94.15%** | +5.73% Global Screening Precision|
| **Precision** | 87.10%                        | **93.80%** | Reduced False Alarm Routing Loss |
| **Recall** | 86.95%                        | **92.45%** | Captured Hidden Attrition Risks  |
| **F1-Score** | 87.02%                        | **93.12%** | Fully Stabilized Operational Engine|

👉 **Visual Artifact Reference:** Check `rf_airline_confusion_matrix.png` in the repository root directory to see the complete True vs. False classification distributions.

---

## 🏢 Executive Insights: Key Passenger Satisfaction Drivers
Based on the extracted model parameters, the top features impacting passenger experience are ranked below:

1. **Inflight Wifi Service:** The single strongest predictor of negative or positive evaluation scores across long-distance routes.
2. **Type of Travel (Business vs. Personal):** Business travel cohorts exhibit significantly more rigid expectations regarding flight scheduling updates and seating space allocation.
3. **Seat Comfort:** A critical entry vector for baseline operational satisfaction.

### 🚀 Strategic Leadership Recommendations
* **Digital Infrastructure Investment:** Allocate capital to upgrade inflight connectivity networks, as internet access is the primary driver of passenger satisfaction.
* **Segment-Specific Inflight Amenities:** Tailor premium seating workflows and on-board quiet zones for business routes to address their unique customer expectations.
