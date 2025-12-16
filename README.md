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

