# 📊 Netflix Userbase Analysis on Google Cloud Platform

This project analyzes a sample Netflix user dataset using end-to-end data engineering and machine learning workflows on **Google Cloud Platform (GCP)**. The goal was to simulate a production-level cloud-based pipeline involving **ETL, LTV prediction, revenue forecasting, user clustering, and visualization**.

---

## 🔧 Tech Stack

- **Google Cloud Storage (GCS)** – Raw data upload and storage
- **Google Cloud Dataflow** – Data transformation and pipeline orchestration
- **BigQuery** – SQL-based analytics and ML modeling
- **BigQuery ML (BQML)** – Regression and clustering models
- **ARIMA** – Time-series revenue forecasting
- **Looker Studio** – Visualization and dashboarding
- **Pandas / Python** – Local data inspection and feature engineering (optional)

---

## 🧾 Dataset Description

- Rows: 2,500 Netflix users  
- Features:
  - Subscription Type (Basic, Standard, Premium)
  - Monthly Revenue
  - Join Date, Last Payment Date
  - Country, Age, Gender, Device Type
  - Plan Duration Days (engineered feature)

Source: [Kaggle – Netflix Userbase Dataset](https://www.kaggle.com/datasets/arnavsmayan/netflix-userbase-dataset/data)

---

## 🔄 ETL Pipeline

- **Extract**: Dataset retrieved from Kaggle and uploaded to GCS.
- **Transform**:
  - Removed meaningless columns (e.g., fixed Plan Duration)
  - Converted categorical features (e.g., Country, Subscription Type) to numeric
  - Calculated `Plan_Duration_Days` = `Last_Payment_Date - Join_Date`
  - Engineered feature: **LTV = Monthly Revenue × Plan Duration (months)**
- **Load**: Cleaned dataset loaded into BigQuery using a custom Dataflow pipeline.

---

## 🤖 Machine Learning Models

### 🎯 LTV Prediction (Regression)

| Model              | Description                                      | Result                |
|--------------------|--------------------------------------------------|------------------------|
| Linear Regression  | Baseline model                                   | Underfit, poor result |
| Boosted Tree Regr. | Non-linear modeling                              | Best performance      |
| DNN Regression     | Deep learning model (overfitting due to small data) | Lower performance     |

---

### ⏳ Revenue Forecasting

- Used **ARIMA** for time-series prediction of monthly revenue
- Trained per country (e.g., Mexico) using historical revenue trends
- Forecasted next 5 months of revenue

---

### 👥 User Segmentation

- Applied **K-Means clustering** to identify key user groups
- Clustered by LTV, age, device, subscription plan, and engagement features
- Findings:
  - Key users prefer **Smartphones**
  - Most popular plan: **Standard**

---

## 📊 Visualizations

Created using **Looker Studio**:
- Revenue growth over time
- Country-level revenue distribution
- Cluster profiles by device & plan

---

## 🧠 Key Learnings

- Understood end-to-end GCP-based data pipelines using real tools (GCS, Dataflow, BigQuery)
- Learned the limitations of deep models on small datasets
- Gained hands-on experience in cloud-native ML (BQML)
- Identified the business value of analytical data engineering


