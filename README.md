# 🛠️ Titanic Survival Prediction with Astro Airflow, Redis, Prometheus & Grafana

An end-to-end machine learning pipeline using **Astro Airflow**, **Redis feature store**, **SQL**, and **ML Monitoring** via **Prometheus and Grafana**, designed to predict Titanic passenger survival.

---

## 🚀 Overview

This project demonstrates a full-stack data engineering and machine learning system using the Titanic dataset. It covers:

- ETL pipeline orchestration using **Astro Airflow**
- Feature storage and retrieval using **Redis**
- Drift detection using **Alibi Detect**
- ML monitoring and dashboards via **Prometheus + Grafana**
- Model serving via a **Flask web app**

---

## 📦 Tech Stack

| Layer               | Tools/Technologies                                      |
|---------------------|--------------------------------------------------------|
| Orchestration       | Astro Airflow (based on Apache Airflow)               |
| Data Storage        | GCP Buckets, PostgreSQL                               |
| Feature Store       | Redis                                                  |
| Drift Detection     | Alibi Detect                                           |
| Monitoring          | Prometheus, Grafana                                    |
| Deployment & Serving| Flask, HTML Frontend                                  |
| Version Control     | GitHub (Code & Data)                                   |

---

## 🧱 Project Architecture

           +--------------------+
           |   GCP Bucket (CSV) |
           +--------------------+
                     |
          ETL (Astro Airflow)
                     |
        +------------+------------+
        |                         |
PostgreSQL DB               Feature Store (Redis)
        |                         |
        |                 +-------------------+
        |                 | Drift Detection   |
        |                 | (Alibi Detect)    |
        |                 +--------+----------+
        |                          |
+-------v--------+        +--------v---------+
| Model Training | <----> | Feature Extraction|
+----------------+        +-------------------+
                     |
               +-----v------+
               | Flask App  |
               +------------+
                     |
            +--------v---------+
            | Prometheus (Metrics)|
            +---------------------+
                     |
            +--------v---------+
            | Grafana Dashboard |
            +------------------+



---

## 🛠️ Key Features

### ✅ ETL with Astro Airflow
- Simple setup using `astro dev init`
- Loads CSV data from GCP bucket into PostgreSQL
- Transforms and formats CSV into SQL-compatible structure

### ✅ Feature Store with Redis
- Fast, scalable alternative to storing features with `.pkl` files
- Optimized for high-speed retrieval and dynamic scaling
- Methods implemented for storing, extracting, and updating features

### ✅ Drift Detection
- Implemented **Alibi Detect** for:
  - **Data drift**: change in input features (X)
  - **Concept drift**: change in relationship between inputs and outputs (X → Y)
- Uses reference (training) vs current (live/testing) data
- Custom drift metrics tracked via Prometheus

### ✅ Model Training Pipeline
- Combines ingestion → processing → training into a unified flow
- Extracts clean features from Redis
- Trains and validates ML model (Titanic survival prediction)

### ✅ Real-Time Predictions with Flask App
- Frontend built with HTML
- Accepts user inputs and returns survival predictions
- Hooks into Redis to access clean features for inference

### ✅ Monitoring with Prometheus & Grafana
- **Prometheus**:
  - Tracks custom metrics (e.g., drift count, prediction count)
  - Provides default system metrics (HTTP traffic, uptime, etc.)
- **Grafana**:
  - Visualizes metrics with dashboards
  - Triggers alerts (e.g., drift count > threshold)

---

## 🧪 Data Source

- Dataset: [Titanic - Machine Learning from Disaster](https://www.kaggle.com/c/titanic)
- Format: CSV
- Stored in GCP Bucket and later ingested into PostgreSQL

---

## 💡 Why Use Redis as a Feature Store?

| Traditional (joblib/pickle) | Redis Feature Store |
|-----------------------------|---------------------|
| Slower for large datasets   | High-speed retrieval |
| Not scalable                | Easily scalable      |
| Manual reprocessing needed  | Efficient updates    |


## 🧭 Future Enhancements

- Integrate Kafka for real-time streaming
- Migrate from Redis to **Feast** for advanced feature store management
- Deploy to GCP and enable cloud-based monitoring
- Add authentication layer to Flask app



