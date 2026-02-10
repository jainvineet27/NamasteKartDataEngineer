# 📘 Retail Lakehouse Pipeline — Medallion Architecture (Bronze → Silver → Gold)
**_Last Updated: 10 February 2026_**

---

# 🌟 Overview

Modern retail companies often operate **disconnected systems**:

- **Online commerce platform**
- **Offline POS store system**

Each system generates **customers**, **products**, and **orders** independently.  
Because there is **no unified data strategy**, the organization faces:

- Duplicate customer records  
- Conflicting product definitions  
- Fragmented order history  
- Unreliable reporting  
- No single source of truth  

This project builds a **Lakehouse Data Pipeline** using **Apache Spark**, following the **Medallion Architecture**, deployed on:

- **Compute:** Databricks / Spark on Docker  
- **Storage:** AWS S3  
- **Format:** Delta Lake  

The goal is to unify, cleanse, and model retail data for analytics and customer insights.

---

# 🎯 Project Objectives

### **1. Master Data Management (MDM)**
Create a **Golden Customer Record** — one identity per customer across online + offline systems.

### **2. Unified Analytics**
Merge all retail data into a single analytical model.

### **3. Customer Retention Strategy**
Enable loyalty scoring, voucher recommendations, and subscription insights.

### **4. Modernize Legacy Systems**
Transform disconnected legacy systems into a **Lakehouse architecture** with scalable ingestion and processing.

---



# 📦 Project Folder Structure (Simplified Tree)

```
project/
│
├── utilities/
│   ├── paths.py
│   ├── io_helpers.py
│   └── __init__.py
│
├── bronze/
│   ├── load_customers.py
│   ├── load_products.py
│   ├── load_orders.py
│   └── __init__.py
│
├── silver/
│   ├── cleanse_customers.py
│   ├── cleanse_products.py
│   ├── cleanse_orders.py
│   └── __init__.py
│
├── gold/
│   ├── curated_customers.py
│   ├── curated_products.py
│   ├── curated_orders.py
│   └── __init__.py
│
└── main.py
```

This tree is clean, readable, and easy to understand at a glance.

---

# 🧰 Development Workflow (PyCharm / VS Code)

You will:

1. Write modular Python code locally  
2. Organize code into utilities, bronze, silver, and gold layers  
3. Submit your job to your **Docker Spark cluster** using `spark-submit`  
4. Avoid copying files manually into containers  

This approach provides:

- Fast development  
- Real distributed execution  
- Easy debugging  
- Scalable architecture  
- Regression testing capability  

---

# 🐳 Running on Docker Spark Cluster

You already have a **Spark Master + Worker** setup running in Docker.

### Submit your job from your laptop:

```bash
spark-submit \
  --master spark://<master-ip>:7077 \
  main.py
```

Spark automatically distributes your Python modules to the workers.

---

# ☁ Ingestion Strategy

## **Real‑World Ingestion (AWS / Azure)**

In production, ingestion would be automated using:

- **AWS S3 Events**  
- **Azure Event Hubs**  
- **Databricks Auto Loader**  
- **Azure Durable Functions**  
- **Scheduled ETL pipelines**  

### Connecting Databricks to S3 (Real‑World Example)

1. Create an **IAM Role** in AWS with S3 access  
2. Configure **External Credentials** in Databricks  
3. Databricks generates a trust policy  
4. Replace the JSON in AWS IAM with the Databricks trust policy  
5. Databricks can now read/write S3 securely  

---

## **Project Simulation (For Learning)**

To simplify the project:

- We simulate **daily ingestion**  
- Using **day‑wise folders** in S3  
- Read incrementally from these folders  

This keeps the project realistic but manageable.

---

# 🧩 Why This Architecture Works

- **Modular code** → easy to extend  
- **PyCharm local development** → fast iteration  
- **Docker Spark cluster** → real distributed execution  
- **Medallion architecture** → industry standard  
- **Delta format** → ACID, time travel, schema evolution  
- **S3 storage** → scalable, cost‑efficient  

This setup supports:

- Regression testing  
- CI/CD integration  
- Future cloud migration  
- Team collaboration  

---

# 🚀 Future Enhancements

- Add Auto Loader for streaming ingestion  
- Implement SCD Type‑2 for customer dimension  
- Add ML models for churn prediction  
- Add Airflow / Databricks Jobs for orchestration  
- Add unit tests with PyTest + Delta Live Tables validation  

---

# 🎉 Conclusion

This project demonstrates how to build a **modern retail Lakehouse** using:

- **Spark**
- **Delta Lake**
- **Medallion Architecture**
- **S3**
- **Docker-based Spark cluster**
- **Modular Python code**

It provides a strong foundation for real‑world data engineering, analytics, and customer intelligence.

