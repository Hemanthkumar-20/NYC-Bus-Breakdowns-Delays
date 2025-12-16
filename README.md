# NYC Bus Breakdown and Delays – Data Analysis Project

## Overview

This project analyzes the **New York City Bus Breakdown and Delays** dataset obtained from [NYC Open Data](https://data.cityofnewyork.us/Transportation/Bus-Breakdown-and-Delays/ez4e-fazm).
The aim is to **understand operational delays, breakdown causes, and borough-level trends**, and to **predict breakdown categories** using machine learning techniques.

---

## 📊 Power BI Dashboard
The complete Power BI report is available here:
🔗 https://drive.google.com/drive/folders/17o3K7GnKxfIv2SgRFJuJBS2Dhgysf2nU?usp=sharing

## Technical Stack

* **Language:** Python 3
* **Libraries Used:**

  * `pandas` – data loading, cleaning, and preprocessing
  * `numpy` – numerical computations
  * `matplotlib`, `seaborn` – data visualization
  * `scikit-learn` – feature encoding, scaling, and machine learning
  * `datetime` – date-time feature parsing

---

## Dataset Information

* **Source:** NYC Open Data Portal
* **File Used:** `Bus_Breakdown_and_Delays.csv`
* **Key Columns:**

  * `Boro` – Borough of NYC where the breakdown occurred
  * `Occurred_On` – Date and time of the breakdown
  * `Reason` – Cause of breakdown or delay
  * `Incident_Number` – Unique identifier
  * `Run_Type`, `Run_Number` – Bus operational details
  * `How_Long_Delayed` – Delay duration
  * `School_Year`, `Bus_Company_Name` – Contextual metadata

---

## Data Preprocessing

* **Column normalization:** Trimmed whitespaces and standardized names.
* **Datetime parsing:** Converted `Occurred_On` to datetime format.
* **Missing value handling:**

  * Removed rows with null critical fields (`Reason`, `Boro`).
  * Imputed or replaced minor missing values in delay duration using median.
* **Feature Engineering:**

  * Extracted **month, day, hour** from `Occurred_On`.
  * Derived categorical target: `Target_Breakdown` (e.g., Mechanical / Non-Mechanical).
  * Calculated **breakdown counts per precinct (`Pct_Breakdown`)** for borough-level aggregation.

---

## Exploratory Data Analysis (EDA)

Performed comprehensive EDA using `matplotlib` and `seaborn`.

**Key Visuals:**

* Breakdown frequency across **boroughs (Boro)**
* Distribution of **delay durations**
* Monthly/seasonal trends in breakdowns
* Top causes of breakdowns and their frequency
* Correlation heatmap of numeric features

**Insights:**

* Most breakdowns occur in **Bronx and Brooklyn**, showing higher fleet density.
* **Mechanical issues** and **traffic delays** are leading causes.
* **Morning hours (7–9 AM)** show peak breakdown frequency.
* Average delay duration tends to be higher for **older bus fleets** and **rainy months**.

---

## Machine Learning Component

A **classification model** was developed to predict the **type of breakdown** (`Target_Breakdown`) using operational and temporal features.

### Model Workflow:

1. **Encoding:** Converted categorical features (Boro, Reason, Run_Type) using `LabelEncoder` / `OneHotEncoder`.
2. **Feature Scaling:** Applied `StandardScaler` for continuous variables.
3. **Train-Test Split:** 80-20 ratio.
4. **Models Tested:**

   * Logistic Regression
   * Random Forest Classifier
   * Decision Tree Classifier
5. **Evaluation Metrics:**

   * Accuracy, Precision, Recall, F1-Score
   * Confusion Matrix

**Best Performing Model:** Random Forest (Accuracy ≈ 87%)
**Key Predictors:** `Boro`, `Reason`, and `How_Long_Delayed`

---

## Results and Insights

* **Borough-level Analysis:** Bronx has the highest average delay time.
* **Seasonal Pattern:** Delays increase during winter months due to weather conditions.
* **Predictive Model:** Random Forest shows high accuracy and robustness for breakdown classification.
* **Operational Recommendation:** Preventive maintenance should prioritize bus depots with historically high breakdown frequency.

---

## Application
The application codes are on **GitHub Repo**:
[Repository](https://github.com/PrasadSimhadri/nyc-application)
