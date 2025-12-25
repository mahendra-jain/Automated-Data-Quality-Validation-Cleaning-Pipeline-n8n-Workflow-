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

![n8n Workflow](Automated Data Quality Monitoring & Cleaning Pipeline (n8n).png)

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
```
# Data Quality Monitoring Workflow

### 4️⃣ IF Condition – Data Quality Decision 🔀

**Condition Logic:**

- **TRUE →** Data quality issues exist  
  - Schema is invalid OR  
  - Null / Duplicate / Outlier count > 0

- **FALSE →** Dataset is already clean

---

### 5️⃣ Clean Dataset Path (No Issues) ✅

If no issues are detected:

📧 A Gmail notification is sent:

> “The dataset has been successfully validated and no data quality issues were detected. Since no issues were found, the original dataset is already clean and required no modifications.”

🛑 Workflow ends here.

---

### 6️⃣ Data Cleaning Logic (Code Node) 🧹

If data quality issues exist:

- Entire rows are removed if they contain:  
  - Null values  
  - Duplicate records  
  - Outliers (based on IQR boxplot method)

Output is a fully cleaned dataset.

---

### 7️⃣ Remove Duplicates Node 🔁

- Prevents previously processed records from being added again.  
- Ensures only new and unique rows enter the clean sheet.

---

### 8️⃣ Append / Update Clean Data in Google Sheets 📥

- Cleaned rows are appended or updated in the Clean Data Sheet.  
- Keeps the dataset continuously refreshed.

---

### 9️⃣ Convert Clean Data to CSV 📁

- Converts the cleaned dataset into a CSV file.  
- Required to send the dataset as an email attachment.

---

### 🔟 Email Notification with CSV Attachment 📧

Sends a detailed email containing:

- Summary of detected data issues  
- Cleaned dataset attached as a CSV file  

**Email Message Example:**

> The original dataset contained data quality issues.  
> The attached file contains the cleaned dataset after removing rows with null key fields, duplicates, and outliers based on the IQR boxplot method. Please find the cleaned dataset attached or open the Google Sheet directly if preferred.

---

### 1️⃣1️⃣ KPI Extraction (Parallel Execution) 📊

A parallel Code Node extracts business KPIs from the cleaned dataset.

**KPIs Calculated:**

- totalRevenue  
- totalOrders  
- avgOrderValue  
- uniqueCustomers  
- avgRevenuePerCustomer  
- ordersByCountry  
- revenueByCountry

---

### 1️⃣2️⃣ KPI Sheet Update 📈

- KPI values are dynamically updated in a Google Sheet.  
- Every workflow execution refreshes KPIs automatically based on latest clean data.

---

### ✨ Key Features

- 🔄 Fully automated scheduled execution  
- 🧪 Advanced data quality validation  
- 🧹 Intelligent row-level data cleaning  
- 📊 Real-time KPI generation  
- 📧 Automated email alerts with attachments  
- 📎 Clean data delivery in CSV format

---

### 🎯 Use Cases

- Data Quality Monitoring Systems  
- ETL / ELT Pre-processing Pipelines  
- Business Reporting Automation  
- Analytics & BI Data Validation  
- Data Engineering & Analytics Portfolios

---

### 📌 Future Enhancements

- Slack / Microsoft Teams notifications  
- Data quality dashboard (Power BI / Looker Studio)  
- Row-level error logging  
- Cloud database integration  
- AI-based anomaly detection

---

### 👤 Author

**Mahendra Jain**  
📊 Data Analyst | Automation & Analytics Enthusiast  

**Skills:**  
SQL • Python • Excel/Google Sheets • Power BI/Looker Studio • n8n

---

## 🔗 Links:

[LinkedIn](https://www.linkedin.com/in/-mahendrajain-/)
[Portfolio](https://mahendrajainportfolio.netlify.app/)
