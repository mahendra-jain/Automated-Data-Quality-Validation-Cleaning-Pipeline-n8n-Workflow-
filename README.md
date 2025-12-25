# 📊 Automated Data Quality Monitoring & Cleaning Pipeline (n8n)

> An end-to-end automated workflow for **data validation, cleaning, KPI generation, and email reporting** using **n8n** and **Google Sheets**

---

## 🚀 Project Overview

This project demonstrates a **fully automated data quality monitoring pipeline** built using **n8n**.  
It continuously validates incoming raw data, detects quality issues, cleans the dataset automatically, generates key business KPIs, and notifies stakeholders via email — all on a scheduled basis.

The workflow runs **without any manual intervention** and ensures that downstream analytics always use **clean, reliable data**.

---

## 🧰 Tech Stack & Tools

- ⚙️ **n8n** – Workflow orchestration & automation  
- 📄 **Google Sheets** – Raw data source, clean data storage & KPI storage  
- 🧠 **JavaScript (Code Nodes)** – Data validation, cleaning & KPI logic  
- 📧 **Gmail** – Automated email notifications  
- 📁 **CSV** – Cleaned data attachment  

---

## 🔁 Workflow Architecture

![n8n Workflow](workflow.png)

> Upload the workflow screenshot as `workflow.png` in the repository root.

---

## 🧩 Complete Workflow Explanation (Step-by-Step)

---

### 1️⃣ Schedule Trigger ⏰
- Triggers the workflow automatically at a defined interval (e.g., **every hour**).
- Enables continuous and automated data quality monitoring.

---

### 2️⃣ Read Raw Data from Google Sheets 📄
- Uses the **Google Sheets – Read Sheet** node.
- Reads the **entire raw dataset** from the source Google Sheet.

---

### 3️⃣ Data Validation (Code Node) 🧠
A JavaScript **Code Node** checks the dataset for data quality issues.

#### Validations Performed:
- ✅ **Schema Validation** (True / False)
- ❌ **Null Value Count**
- 🔁 **Duplicate Row Count**
- 📉 **Outlier Count** (IQR / Boxplot method)

#### Example Output:
```json
{
  "schemaValid": false,
  "nullCount": 2,
  "duplicateCount": 1,
  "outlierCount": 1
}
### 4️⃣ IF Condition – Data Quality Decision 🔀
