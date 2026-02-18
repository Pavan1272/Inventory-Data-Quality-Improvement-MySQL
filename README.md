# Inventory Data Quality Improvement using MySQL

## Project Overview
This project focuses on performing structured data validation, cleansing, and transformation on an inventory dataset using MySQL to ensure accuracy, consistency, and business reliability. The objective was to identify inconsistencies such as missing SKUs, negative quantities, incorrect pricing, and profit mismatches, and to produce a cleaned and validated inventory table ready for business analysis.

---

## Technologies Used
- MySQL 8.0
- SQL (DDL & DML)
- GitHub

---

## Dataset Information
The dataset contains the following columns:

- SKU
- Quantity
- Price
- Cost
- Profit
- OrderDate

---

## Data Quality Checks Performed
✔ Missing SKU detection  
✔ Negative or zero quantity validation  
✔ Negative price and cost validation  
✔ Profit mismatch verification  
✔ Date format validation  

---

## Data Cleaning Steps
- Removed records with missing SKUs
- Removed invalid quantity records
- Corrected negative price and cost values
- Recalculated profit using formula:
  
  `Profit = Price - Cost`

- Applied constraints to maintain future data integrity

---
## Author
Pavan Attarkar
Aspiring Data Analyst | SQL | Data Cleaning | Business Intelligence

## 📊 Final Validation Summary

```sql
SELECT 
COUNT(*) AS TotalRecords,
SUM(Quantity) AS TotalQuantity,
SUM(Profit) AS TotalProfit,
SUM(Price * Quantity) AS TotalRevenue
FROM inventory_clean;

SELECT SKU,
SUM(Profit * Quantity) AS TotalProductProfit
FROM inventory_clean
GROUP BY SKU
ORDER BY TotalProductProfit DESC
LIMIT 5;

