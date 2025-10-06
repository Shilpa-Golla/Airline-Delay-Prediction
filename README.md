# Project – Airline Delay Analysis  
**Course:** Machine Learning  
**Student:** Shilpa  
**Submission Date:** 06.10.2025  

---

##  Project Overview
This project analyzes and predicts flight delays using the **Airline Delay Causes Dataset**.  
The objective is to explore patterns behind flight delays and develop a **machine learning model** to predict whether a flight will be **delayed (>15 minutes)** or **on-time**.  

The analysis combines **Exploratory Data Analysis (EDA)**, **feature engineering**, and **predictive modeling** to uncover key delay causes and improve operational understanding.  

---

##  Objectives
- Clean and preprocess the flight delay dataset.  
- Perform detailed **Exploratory Data Analysis (EDA)** to identify delay trends.  
- Build a **classification model** to predict delayed flights.  
- Interpret model results using metrics and feature importance.  
- Provide actionable insights and recommendations for delay management.  

---

##  Dataset
- **Source:** [Airlines Delay Causes – Kaggle](https://www.kaggle.com/datasets/giovamata/airlinedelaycauses)  
- **File Used:** `DelayedFlights.csv`  
- **Size:** ~1.9 million records  
- **Key Columns:**  
  `Year`, `Month`, `DayOfWeek`, `CRSDepTime`, `DepDelay`, `ArrDelay`,  
  `UniqueCarrier`, `Origin`, `Dest`, `Distance`, `CarrierDelay`, `WeatherDelay`, etc.  

---

## Steps and Methodology

### Data Preprocessing
- Removed **cancelled and diverted** flights.  
- Filled missing delay cause columns with `0`.  
- Dropped unnecessary index columns.  
- Created a new target variable `IsDelayed` (1 if `DepDelay > 15`).  
- Capped extreme outliers (`DepDelay` between -60 and 600 minutes).  

### Exploratory Data Analysis (EDA)
- Visualized delay rates by **Month**, **DayOfWeek**, **Hour**, **Carrier**, and **Airport**.  
- Identified **seasonal patterns** and **congestion peaks**.  
- Analyzed **delay causes** (Late Aircraft, Carrier, NAS).  

###  Feature Engineering
- Extracted new features:  
  - `DepHour` (departure hour from CRSDepTime)  
  - `IsDelayed` (binary target)  
- Encoded categorical variables such as `UniqueCarrier`, `Origin`, and `Dest`.  

###  Model Building
- **Model Used:** Random Forest Classifier  
- **Target:** `IsDelayed`  
- **Metrics:** Accuracy, Precision, Recall, F1-score, ROC-AUC  
- **Performance Summary:**  
  - Accuracy: **59.6%**  
  - Precision (Delayed): **0.70**  
  - Recall (Delayed): **0.62**  
  - ROC–AUC: **0.624**  

### Feature Importance
Top predictive features:
- `Month`
- `CRSDepHour`
- `UniqueCarrier`
- `Origin` and `Dest` airports  

These confirm that **time, season, and carrier operations** strongly influence flight delays.

---

## Key Insights
- Around **65.9%** of flights were delayed by more than 15 minutes.  
- **Evening flights** and **winter months** showed higher delays.  
- **Busy airports** like **ORD** and **ATL** have higher delay frequencies.  
- **Late aircraft** and **carrier-related issues** are top contributors to total delay minutes.  

---

## Recommendations
1. **Schedule Optimization:** Avoid tight connections in peak hours (late evening).  
2. **Carrier Management:** Improve fleet scheduling and turnaround time for high-delay carriers.  
3. **Airport Operations:** Increase runway and ground resource allocation at congested airports.  
4. **Predictive Monitoring:** Use this model in dashboards to flag flights with high delay risk.

---

## Future Work
- Add external features such as **weather data** and **air traffic information**.  
- Try **Gradient Boosting (XGBoost/LightGBM)** for improved ROC–AUC.  
- Perform **hyperparameter tuning** for better generalization.  
- Extend to **regression modeling** to predict delay minutes.

---

## Files in Repository
- `Shilpa_3_Project.ipynb` → Main Jupyter Notebook  
- `DelayedFlights.csv` → Dataset (not uploaded if large, link provided)  
- `README.md` → Project documentation  

---

## Conclusion
The project demonstrates that flight delays can be **partially predicted** using scheduled, operational, and carrier-based features.  
While the model shows moderate accuracy (ROC–AUC = 0.624), it provides strong evidence for the key factors influencing delays and supports data-driven operational decisions in the airline industry.
