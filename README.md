# Automated Data Quality Validation & Cleaning Pipeline (n8n Workflow)

## 📘 Overview
This n8n workflow automatically validates an incoming dataset, identifies data quality issues, sends notifications, and generates a fully cleaned dataset. It is designed to run on a schedule and provide real-time insights into data health.

---

## 🎯 Features

### ✔ Schema Validation
Ensures all required columns are present.

### ✔ Null Value Detection
Detects missing or null-equivalent values in key fields.

### ✔ Duplicate Detection
Identifies repeated `order_id` entries.

### ✔ Outlier Detection (Boxplot / IQR Method)
Dynamically calculates:
- Q1
- Q3
- IQR
- Lower bound
- Upper bound

Outliers falling outside these bounds are flagged.

### ✔ Auto-Cleaning Engine
Automatically removes:
- Rows with null key fields  
- Duplicate order IDs  
- Statistical outliers (IQR method)

### ✔ Email Notification System
Two types of automated email alerts:
- **Issues Found:** Summary of nulls, duplicates, outliers  
- **No Issues:** Confirms the dataset is already clean

### ✔ Cleaned Dataset Export
A cleaned CSV/XLSX file is generated and attached in email for downstream use.

---

## 🏗 Workflow Architecture

<img width="1689" height="380" alt="image" src="https://github.com/user-attachments/assets/81c2b63f-e749-4f34-ac74-e8c12df1c840" />


---

## 📊 Data Quality Checks Performed

| Check Type          | Description |
|---------------------|-------------|
| **Schema Validation** | Ensures required fields exist |
| **Null Detection**     | Flags missing/blank key fields |
| **Duplicate Detection** | Identifies repeated order IDs |
| **Outlier Detection** | Boxplot (IQR) based outlier filtering |
| **Cleaning Logic** | Drops invalid, duplicate, or outlier rows |

---

## 🧮 Outlier Detection Formula (IQR)
Q1 = median(lower half of dataset)
Q3 = median(upper half of dataset)
IQR = Q3 - Q1

Lower Bound = Q1 - 1.5 × IQR
Upper Bound = Q3 + 1.5 × IQR


Outliers = values outside `[Lower Bound, Upper Bound]`.

---

## 📁 Cleaned Dataset Output
A cleaned dataset is:
- Written into a second Google Sheet tab
- Exported as a downloadable file
- Attached automatically to email notifications

---

## 📨 Email Notifications

### If issues exist:
- Summary of:
  - Null values  
  - Duplicate order IDs  
  - Outliers  
- Cleaned dataset file attached

### If **no issues exist**:
Message example:
Dataset validation successful — No issues detected


---

## ⚙ Technologies Used

- **n8n** – Workflow orchestration
- **Google Sheets API** – Data input/output
- **Gmail API** – Email alerts
- **JavaScript (Code Nodes)** – Data validation & cleaning logic

---

## 🚀 How to Use

1. Connect Google Sheets and Gmail credentials in n8n  
2. Provide a spreadsheet containing the required columns  
3. Import this workflow  
4. Configure schedule as desired  
5. Receive automated validation summaries and cleaned dataset files  

---

## 🔮 Future Enhancements (Optional)

- Slack alerts  
- Data drift monitoring  
- Looker Studio dashboard integration  
- Multi-sheet ingestion support  

---

## 🏁 Summary
This project provides an automated, production-ready data quality pipeline that validates, cleans, and exports datasets with minimal human intervention — ideal for analytics workflows and ETL preparation.
