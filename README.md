# 🚕 SIC_2025 – NYC Taxi Trip Data Analysis

**Capstone Project - Samsung Innovation Campus (Big Data Course)**  
**Team 1: 4 người**  
**Date:** August 2025  

---

## 📘 Project Overview

This project analyzes and predicts taxi demand across New York City using the **TLC Trip Record Data (2024)**.  
By leveraging **Big Data** and **Machine Learning**, the project aims to optimize vehicle allocation across regions and time periods, helping improve transportation efficiency and passenger experience.

---

## 🎯 Objectives

- Analyze mobility demand patterns across time and location.
- Identify high-demand areas and peak hours for different taxi types.
- Build **predictive models** to forecast taxi demand levels.
- Visualize data to support operational decision-making.
- Provide recommendations for efficient taxi allocation.

---

## 🗂️ Datasets

Source: [NYC TLC Trip Record Data](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)

| Dataset | Description | Key Fields |
|----------|--------------|-------------|
| **Yellow Taxi Data** | Traditional taxis serving all 5 boroughs. | pickup/dropoff time, distance, PULocationID, DOLocationID |
| **Green Taxi Data** | Green taxis serving outer boroughs (Bronx, Brooklyn, Queens). | Similar fields as Yellow Taxi |
| **High Volume FHVHV** | Ride-hailing services (Uber, Lyft, Via, etc.). | trip_miles, trip_time, company license, pickup/dropoff IDs |

---

## ⚙️ Data Pipeline

### 1. **Ingestion**
- Load `.parquet` data into **HDFS** using `hdfs dfs -put`.
- Managed and analyzed in **PySpark** environment.

### 2. **Transformation**
- Data cleaning:
  - Remove null/invalid entries.
  - Filter out unrealistic speeds and trip lengths.
- Feature engineering:
  - Extract `hour`, `weekday`, `month`, and holiday tags.
  - Create lag features (`lag_24hr`, `lag_168hr`).

### 3. **Storage**
- Store cleaned datasets in **Parquet** format for efficient querying.

---

## 📊 Exploratory Data Analysis (EDA)

- **Average daily trips by borough**  
  - Manhattan and areas near **JFK** show the highest taxi density.  
  - Staten Island and eastern Bronx remain low-demand zones.

- **Temporal patterns**
  - Peak hours: 16h–20h  
  - Busiest days: Friday and Saturday

Visualizations include:
- Heatmaps of trips by hour & weekday  
- Distribution plots of daily trips per borough

---

## 🤖 Machine Learning Models

| Taxi Type | Model | Accuracy | Notes |
|------------|--------|-----------|-------|
| **Yellow Taxi** | Random Forest Classifier | 66.3% | Predicts demand levels (Very Low → Very High) |
| **Green Taxi** | Clustering (K-Means) + Random Forest | F1 = 0.71 (best cluster) | Combines spatial clustering and classification |
| **High Volume (FHVHV)** | Random Forest | 80.2% | Scalable model trained on 200M+ records |

### Key Features:
- Temporal: `hour`, `weekday`, `month`, `holiday_type`
- Spatial: `PULocationID`
- Historical: `lag_24hr`, `lag_168hr`

---

## 💻 Tools & Technologies

- **Languages:** Python (PySpark, Pandas, Scikit-learn, Matplotlib, Seaborn)
- **Frameworks:** Hadoop HDFS, Apache Spark
- **Visualization:** Matplotlib, Seaborn, GeoPandas
- **Web Demo:** Flask + HTML/CSS for ML model interaction

---

## 🌐 Web Demo

A simple interactive web demo was developed to:
- Input pickup time and zone.
- Predict taxi demand level.
- Display recommendation for optimal vehicle allocation.

---

## 📈 Results & Insights

- Clear temporal and spatial demand patterns.
- Machine Learning models can effectively predict demand peaks.
- Proposed framework supports **dynamic taxi allocation** and **data-driven policy making**.

---

## 🚀 Future Improvements

- Incorporate **weather and event data** to enhance prediction accuracy.
- Apply **deep learning** models for spatiotemporal prediction.
- Develop **real-time dashboards** for transport authorities.

---

## 🏆 Acknowledgments

This project was conducted under the **Samsung Innovation Campus (Big Data Program)**.  
We sincerely thank our instructors and reviewers for guidance and feedback.

---

© 2025 Samsung Innovation Campus - Team SIC_2025

