# 🌊 Tsunami Prediction ML Model from Seismic Data

This project explores whether **tsunami potential** can be predicted **solely from seismic characteristics**.  
Using machine learning classification models, the goal is to determine if an earthquake is likely to generate a tsunami based on measurable seismic parameters.

The final model achieves **90% reliability (F1-score = 0.90)** and **95% sensitivity (Recall = 0.95)** — delivering a *safety-first* solution designed to prioritize the detection of life-threatening events.

---

## Project Overview

- **Objective:** Predict tsunami potential from seismic features only.  
- **Dataset:** *Global Earthquake–Tsunami Risk Assessment Dataset*  
- **Records:** 782 earthquakes (2001–2022)  
- **Coverage:** Global (Lat: -61.85° → 71.63°, Lon: -179.97° → 179.66°)  
- **Target variable:** Binary tsunami indicator  
- **Features:** 13 seismic attributes (magnitude, depth, intensity metrics)  
- **Class distribution:** 38.9% tsunami events vs. 61.1% non-tsunami events  
- **Missing values:** None — 100% complete dataset  

---

## Dataset Sources

https://www.kaggle.com/datasets/ahmeduzaki/global-earthquake-tsunami-risk-assessment-dataset

https://github.com/fraxen/tectonicplates

## Model Overview

The project tested **8 different ML models**, including Random Forest, Gradient Boosting, and Logistic Regression.  
After systematic benchmarking and tuning, the **Gradient Boosting Classifier** emerged as the optimal model.

| Metric | Score |
|:-------|:------:|
| **F1-score** | 0.90 |
| **Recall (Tsunami)** | 0.95 |
| **ROC-AUC** | 0.9011 |

**Reliability:**  
Performance on the test set closely matches cross-validation results (CV F1 = 0.9047), confirming model generalization and stability.

---

## Safety-First Philosophy

In tsunami prediction, **missing a real event (False Negative)** has catastrophic consequences.  
Therefore, the model was explicitly optimized for **Recall**, not pure accuracy.

| Error Type | Meaning | Cost |
|-------------|----------|------|
| **False Positive (FP)** | Predicts tsunami when none occurs | Inconvenience |
| **False Negative (FN)** | Misses a real tsunami | Disaster — lives at risk |

→ The model detects **95% of real tsunamis**, accepting moderate false positives to ensure human safety.

---

## Technical Highlights

This project demonstrates advanced **data science and engineering competencies**:

- 🗺️ **Geospatial Feature Engineering:**  
  Integrated tectonic plate data with GeoPandas and computed `distance_to_fault_km` using CRS projection and geodesic distance.

- 🔍 **Exploratory Data Analysis (EDA):**  
  Identified and removed pre-2012 biased records to prevent spurious correlations (data leakage).

- 🧱 **Robust Validation:**  
  Implemented **Repeated Stratified K-Fold (10×3)** for stable metrics on a small, imbalanced dataset.

- 🔒 **Leak-Proof Pipelines:**  
  Used `sklearn.pipeline` to apply all preprocessing (scaling, encoding) only on training folds.

- ⚙️ **Targeted Hyperparameter Tuning:**  
  Focused on top models (Gradient Boosting, Random Forest) via `GridSearchCV`.

- 📈 **Metric-Driven Decision Making:**  
  Prioritized Recall to align with the *safety-first* philosophy.

- 🧭 **Model Interpretation:**  
  Framed recall–precision trade-offs as deliberate, risk-aware design choices.

---

## Results Summary

✅ **High F1-score (0.90)** — overall robust classification  
✅ **95% Recall on tsunami events** — life-saving sensitivity  
✅ **Stable CV vs. Test performance** — no overfitting  
✅ **Scientific rigor** — leakage-proof pipeline and validation  

This model correctly classifies about **9 out of 10 earthquakes** and **detects 19 out of 20 tsunamis**, making it a reliable tool for early tsunami risk assessment.


---

## 🧰 Tools & Libraries

- **Python 3.10+**
- `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `seaborn`
- `geopandas`, `shapely`, `pyproj`
- `GridSearchCV`, `RepeatedStratifiedKFold`, `Pipeline`

---

## 👤 Author

**Victor MICHELON**  
Data Science & Engineering Student  
🔗 [Portfolio](https://victor-michelon.github.io/Victor_MICHELON_Portfolio.github.io/)

