# 📊 Power-BI – Sales & Orders Data Transformation & Analysis

A complete Power BI solution that transforms raw CSV files into a clean analytical model for sales performance, profit analysis, and monthly target tracking.

## 📑 Table of Contents
- [Project Overview](#project-overview)
- [Data Sources & Architecture](#data-sources--architecture)
- [Data Transformation ETL](#data-transformation-etl)
- [Data Model & DAX](#data-model--dax)
- [Dashboard Features](#dashboard-features)
- [Key Insights](#key-insights)
- [How To Use](#how-to-use)

---

## 🎯Project Overview
- **Business Problem:** Raw sales and order data existed in multiple CSV files with inconsistent formats, making analysis difficult.
- **Objective:** Clean, merge, and model the datasets to enable category‑wise profit analysis, state‑level filtering, and monthly target comparison.
- **Target Audience:** Sales Managers, Business Analysts, Decision‑Makers.

---

## 🗃️ Data Sources & Architecture
- **Source Files:**
  - List of Orders.csv  
  - Order Details.csv  
  - Sales Target.csv  
- **Data Volume:**
  - Orders: 500 rows (limited)
  - Order Details: ~1000 rows
  - Sales Target: 12 monthly records
- **Storage Mode:** Import Mode (Power BI Desktop)

---

## ⚙️ Data Transformation ETL
**Tool Used:** Power Query Editor

### Key Transformations
- Limited List of Orders to **first 500 rows**
- Converted data types:
  - Order Date → Date
  - Amount & Target → Fixed Decimal Number
- Applied **Proper Case** to CustomerName
- Created:
  - **Location** = City, State
  - **Profit Margin** = Profit / Amount
- Added **Profit Status** using conditional logic:
  - Profit < 0 → Loss  
  - Profit = 0 → Break‑Even  
  - Profit > 0 → Profit
- Merged List of Orders + Order Details → **Orders Data**
- Removed duplicates and handled missing values
- Sorted Orders Data by **Order Date (Descending)**
- Filtered orders for **Tamil Nadu**
- Grouped data to create:
  - Count of Order ID  
  - Average Profit by Category  
  - Total Amount by Sub‑Category  
  - Monthly Total Target  

---

## 🧠  Data Model & DAX
### Model Type
Simple star‑schema‑like model.

### Fact Table
- Order Details

### Dimension Tables
- List of Orders  
- Sales Target  

### Relationships
- List of Orders (Order ID) → Order Details (Order ID)  
- Order Details (Category) → Sales Target (Category)

### Sample Measures
```dax
Total Amount = SUM('Order Details'[Amount])
Total Profit = SUM('Order Details'[Profit])
```
## 🖥️ Dashboard Features

### Page 1: Overview
- Total Sales, Total Profit, Total Orders
- Category‑wise Profit
- State‑level filtering (Tamil Nadu)

### Page 2: Deep Dive
- Sub‑Category analysis
- Profit Margin distribution
- Conditional Profit Status visuals

### Page 3: Targets
- Monthly Target vs Actual
- Category‑wise performance
- Trend charts with drill‑down

---

## 💡 Key Insights
- Electronics shows the highest average profit.
- Furniture has high order volume but moderate profit.
- Clothing has lower profit margins.
- Tamil Nadu contributes significantly to total orders.
- Monthly targets vary, enabling performance comparison.

---

## 🚀 How To Use
1. Install the latest Power BI Desktop.
2. Download the `.pbix` file from the repository.
3. Go to **File → Options → Data Source Settings** and update the CSV file paths.
4. Click **Refresh** to load your data.
5. Use slicers and filters to explore insights interactively.


