# Hazardous-Road-Segment-Prediction

Perfect! I’ve taken note of all the details you’ve shared: the **EDA findings**, **problem statement**, and **dataset info**. Using your preferred README structure, I can now draft a polished, end-to-end README for your **Hazardous Road Segment Prediction Project**. Here’s a first full draft:

---

# Hazardous Road Segment Prediction - Telematics Analysis & Predictive Modeling

A comprehensive end-to-end machine learning project demonstrating exploratory data analysis (EDA), data cleaning, feature engineering, and predictive modeling using telematics data from ALTRON.

**Model Performance:** RandomForest: 92% Accuracy | GradientBoosting: 99% Accuracy | AdaBoost: 95% Accuracy (ROC-AUC up to 1.0)
**Dataset:** 58,426 telematics events

---

## Overview

This project performs a complete data science workflow on vehicle telemetry data:

* **Exploratory Data Analysis (EDA)** – Understand driving patterns, incident hotspots, and temporal trends
* **Data Cleaning & Preparation** – Handle missing values, remove redundant columns, impute unidentified road names
* **Feature Engineering** – Extract time-based features, compute speed deviation, total harshness, and g-force metrics
* **Categorical Encoding** – Convert categorical variables for modeling
* **Model Training & Evaluation** – Train and compare 3 classifiers: RandomForest, GradientBoosting, AdaBoost
* **Prediction & Deployment** – Generate predictions for hazardous road segments

**Purpose of the Model:**
"Our model predicts hazardous road segments using vehicle telematics data by analyzing speed, braking, turning, g-forces, and GPS location. The final model outputs predictions and probability scores, enabling proactive, evidence-based interventions to improve road safety and reduce RAF payouts."

---

## Quick Start

### Prerequisites

* Python 3.8+
* pip (Python package manager)

### Step 1: Install Dependencies

```bash
pip install pandas numpy scikit-learn joblib streamlit
```

### Step 2: Download Dataset

Telemetry dataset from ALTRON:

* `telematics.csv` (main dataset)
* Supplementary dataset (optional)

Place the dataset in a `data/` folder:

```
project/
├── data/
│   └── telematics.csv
├── notebook/
│   └── telematics_analysis.ipynb
└── models/
```

### Step 3: Run Notebook

```bash
jupyter notebook notebook/telematics_analysis.ipynb
```

Click **Cell → Run All** or press `Ctrl+Shift+Enter`.

---

## Project Structure

```
hazardous_road_prediction/
├── notebook/
│   └── telematics_analysis.ipynb   # Main notebook (run this!)
├── models/
│   └── best_pipeline.joblib        # Saved ML model
├── data/
│   └── telematics.csv              # Telematics dataset
├── app.py                          # Streamlit app
└── README.md                       # This file
```

---

## Notebook Contents

1. **Setup & Data Ingestion**

   * Import libraries (pandas, numpy, scikit-learn, joblib)
   * Load dataset and display shape, info, and sample records

2. **Data Cleaning & Feature Preparation**

   * Drop redundant/null columns
   * Impute missing/unidentified road names
   * Convert `unitdatetime` to datetime, extract `hour_of_day` and `day_of_week`
   * Rename g-force columns for clarity

3. **Exploratory Data Analysis (EDA)**

   * Average speed: 29.43 km/h, with varied driving conditions
   * Hotspots: "5th Street" (Wynberg), "Kelvin Road" (Bramley), etc.
   * Temporal trends: rush-hour peaks at 8 AM, 2 PM, 6 PM
   * Insights on harsh driving incidents, speed deviations, and total harshness

4. **Feature Engineering**

   * `speed_deviation` = `speed` - `roadspeed`
   * `total_harshness` = sum of harsh_acceleration, hard_braking, sharp_left_turn, sharp_right_turn
   * `road_present` flag to indicate road identification
   * `harsh_count` to quantify aggressive maneuvers

5. **Preprocessing & Encoding**

   * StandardScaler for numeric features
   * OneHotEncoder for categorical features (`hour_of_day`, `day_of_week`, `municipality`, `suburb`, `town`, `road_present`)

6. **Model Training & Evaluation**

   * Trained 3 classifiers:

     * RandomForest (95-97% accuracy)
     * GradientBoosting (**selected for best performance, 99% accuracy**)
     * AdaBoost (good performance on certain classes, 95% accuracy)
   * Evaluation metrics: precision, recall, f1-score, ROC-AUC
   * GradientBoosting selected for deployment due to high accuracy, minimal overfitting, and robustness

7. **Prediction & Deployment**

   * Streamlit app (`app.py`) allows input of telematics features and outputs:

     * **Hazard Level:** Low / Medium / High
     * **Probability Confidence**
   * Example: Hazard Level: Medium | Probability Confidence: 0.657

---

## Key Insights & Conclusions

* Identified **road and suburb hotspots** provide actionable targets for safety campaigns or infrastructure improvements
* **Temporal patterns** reveal peak risk times, enabling better traffic management
* Feature engineering with **g-force metrics** captures driving behavior accurately
* **Machine learning models** can detect hazardous segments proactively, supporting evidence-based interventions

---

## Troubleshooting

* **FileNotFoundError:** Ensure dataset is in `data/` folder
* **ModuleNotFoundError:** Install required packages with `pip install pandas numpy scikit-learn joblib streamlit`
* **Streamlit app issues:** Ensure `models/best_pipeline.joblib` exists and notebook runs without errors

---

## Data Summary

* **Training Data:** 58,426 records
* **Features:** 28 telemetry & derived features
* **Target:** `classification` (hazardous road segments)
* **Numeric Features:** speed, roadspeed, g-force metrics, odometer, battery_voltage_value, etc.
* **Categorical Features:** hour_of_day, day_of_week, municipality, suburb, town, road_present

---

## Learning Outcomes

After completing this project, you will understand:

* Data exploration and driver behavior analysis
* Data cleaning, imputation, and feature engineering
* Machine learning model selection and evaluation
* Building an end-to-end predictive pipeline with deployment

---

## Resources

* ALTRON Telematics Dataset
* Pandas, NumPy, Scikit-learn Documentation
* Streamlit Documentation

---

## Expected Output

* Dataset loaded: 58,426 records
* Missing values handled, redundant columns removed
* Features engineered successfully
* 3 models trained and evaluated
* Selected model: GradientBoosting
* Streamlit app predicts hazard level with confidence score

---

## Author

**Sinenhlanhla Nsele**
**Nonhlanhla Magalula**
**Thandiwe Mkhabela**
**Seema Thabiso**

---


