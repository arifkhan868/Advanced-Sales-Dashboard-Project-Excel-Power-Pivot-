# 📊 Excel PowerPivot Sales Analytics Dashboard

### 🧑‍💻 Author: **Ariful Islam**  
### 🗓️ Year: 2023–2024  
### 💼 Tools: Excel Power Pivot | Power Query | DAX | PivotCharts

---

## 🧠 Project Overview
This project demonstrates how Excel can be transformed into a full-fledged Business Intelligence (BI) platform using **Power Pivot** and **DAX**.  
It features a relational data model, advanced DAX measures, and an interactive dashboard that delivers deep business insights — all inside Excel.

The dashboard analyzes multi-year sales data, comparing revenue growth, customer behavior, and product performance. It’s designed to be **portfolio-ready**, showcasing both technical skill and business acumen.

---

## 🚀 Key Highlights
✅ **Built Entirely in Excel:** No external BI tools — all visuals, KPIs, and DAX logic implemented directly in Excel Power Pivot.  
✅ **End-to-End BI Workflow:** Data import → Cleaning → Modeling → DAX → Visualization.  
✅ **Advanced DAX:** Context-aware measures using `SUMX()`, `CALCULATE()`, and `DISTINCTCOUNT()`.  
✅ **Dynamic Dashboard:** Interactive slicers for Year, Region, Gender, and Category.  
✅ **Professional Design:** Clean layout with KPI cards, charts, and demographic visuals.

---

## 🧩 Data Model Architecture
### 📚 Tables
| Table | Description |
|--------|-------------|
| **Sales** | Transaction-level data (OrderID, Date, ProductID, CustomerID, Quantity, UnitPrice) |
| **Products** | Product details (ProductName, Category) |
| **Customers** | Customer demographics (Region, Gender, Age) |
| **Calendar** | Generated date table for time intelligence (Year, Month, Quarter, IsWeekend) |

### 🔗 Relationships
```
Sales[ProductID]   → Products[ProductID]
Sales[CustomerID]  → Customers[CustomerID]
Sales[Date]        → Calendar[Date]
```

All relationships are **one-to-many**, forming a star schema optimized for DAX performance.

---

## ⚙️ Data Processing Workflow
1. **Data Cleaning (Power Query):** Removed duplicates, fixed data types, and standardized category names.  
2. **Modeling (Power Pivot):** Established relationships and built calculated columns (Revenue, Year, Month).  
3. **Measure Design (DAX):** Built KPIs using iterator and filter functions for dynamic aggregation.  
4. **Visualization:** Created KPI cards, charts, and slicers with conditional formatting and data-driven labels.

---

## 🧮 Advanced DAX Measures

### 🔢 Core KPIs
```DAX
Total Units Sold := SUM(Sales[Quantity])

Total Revenue := SUMX(Sales, Sales[Quantity] * Sales[UnitPrice])

Avg Revenue per Customer := DIVIDE([Total Revenue], DISTINCTCOUNT(Sales[CustomerID]))

Avg Revenue per Product := DIVIDE([Total Revenue], DISTINCTCOUNT(Sales[ProductID]))
```

### 📆 Time Intelligence
```DAX
Revenue 2023 := CALCULATE([Total Revenue], YEAR(Sales[Date]) = 2023)
Revenue 2024 := CALCULATE([Total Revenue], YEAR(Sales[Date]) = 2024)

YOY Growth % :=
VAR Prev = CALCULATE([Total Revenue], SAMEPERIODLASTYEAR(Calendar[Date]))
RETURN IF(NOT(ISBLANK(Prev)), DIVIDE([Total Revenue] - Prev, Prev), BLANK())
```

### ⏰ Behavioral Metrics
```DAX
Revenue Weekend := CALCULATE([Total Revenue], FILTER(Calendar, Calendar[IsWeekend] = TRUE()))
Revenue Weekday := CALCULATE([Total Revenue], FILTER(Calendar, Calendar[IsWeekend] = FALSE()))
```

### 🧭 Dimensional Analysis
```DAX
Top Customers := TOPN(5, VALUES(Customers[CustomerName]), [Total Revenue], DESC)
Top Products := TOPN(10, VALUES(Products[ProductName]), [Total Revenue], DESC)
```

---

## 📸 Dashboard Overview
![Dashboard Screenshot](workbook/Dashboard.PNG)

### 🧭 Key Visuals
- **KPI Cards:** Total Units, Total Revenue, YOY Growth %, Avg per Customer/Product.
- **Trend Analysis:** Monthly revenue comparison (2023 vs 2024).
- **Customer Segmentation:** Gender, Region, Age group revenue contribution.
- **Product Insights:** Top 10 products by revenue.
- **Customer Performance:** Top 5 customers driving sales.
- **Behavioral Insight:** Weekday vs Weekend revenue breakdown.

---

## 📊 Business Insights
📈 **YOY Growth:** +14.58% revenue increase from 2023 → 2024.  
👩‍🦰 **Demographics:** Female customers contribute ~65% of total revenue.  
🌍 **Regional:** West region outperforms with highest revenue share.  
🕒 **Time Pattern:** 71% of total sales occur on weekdays.  
🏆 **Best Products:** Vacuum Cleaner, Yoga Mat, Tennis Racket.  
💰 **Top Customers:** James Adams, Kimberly Cook, Benjamin Stewart.

---

## 📂 Repository Structure
```
excel-powerpivot-sales-dashboard/
├── data/                       # Sample anonymized CSVs (optional)
├── workbook/
│   ├── Excel Dashboard_Project.xlsx  # Main dashboard file
│   └── Dashboard.PNG                 # Dashboard preview
├── docs/
│   ├── DAX-measures.md               # Detailed measure documentation
│   ├── data-model.md                 # Schema and relationship details
│   └── deployment.md                 # Sharing & publishing guide
└── README.md
```

---

## 🔐 Data Privacy & Reproducibility
> ⚠️ All data in this project is **anonymized & simulated** for educational and portfolio purposes.

To replicate:
1. Load CSVs into Power Query.
2. Build relationships in Power Pivot.
3. Copy the provided DAX measures.
4. Design dashboard layout with PivotCharts & slicers.

---

## 🧠 Technical Deep Dive
### Why `SUMX()` and `DISTINCTCOUNT()`?
- `SUMX()` performs row-level iteration, ensuring dynamic calculations for each filter context.
- `DISTINCTCOUNT()` ensures accurate KPI ratios (e.g., per customer/product) by removing duplicates.
- Combined, they make the dashboard **filter-aware** and **context-sensitive**.

**Example Insight:** When filtering by Region = “West”, all KPIs recalculate automatically based on the applied context — no manual recalculation needed.

---

## 🧰 How to Open & Use
1. Open `Excel Dashboard_Project.xlsx` in **Excel 2016+** or **Microsoft 365**.
2. Enable Power Pivot & Power Query add-ins if prompted.
3. Click **Manage Data Model** to inspect table relationships.
4. Use slicers to explore the dashboard interactively.

---

## 🪄 Design Enhancements
- Consistent color palette and typography for corporate look.
- Conditional formatting for KPIs (green/red indicators for growth).
- Dynamic titles and year-based switching using cell references.
- Transparent shapes for modern dashboard aesthetics.

---

## 📢 LinkedIn Showcase Post (Ready-to-Use)
**Header:**
🚀 *Excel Power Pivot + DAX = Full BI Dashboard!* 🔥

**Body:**
I created a fully interactive **Sales Analytics Dashboard** using only Excel Power Pivot & DAX — no Power BI!  
It covers revenue growth, customer demographics, product insights, and time-based patterns with advanced DAX measures like `SUMX`, `DISTINCTCOUNT`, and `CALCULATE`.

বাংলা: আমি Excel (Power Pivot + DAX) ব্যবহার করে একটি professional Sales Dashboard তৈরি করেছি যা সম্পূর্ণ interactive এবং portfolio-ready। 💼

**#Excel #PowerPivot #DAX #Dashboard #DataAnalytics #Portfolio #PowerQuery**

---

## 📜 License
Released under the **MIT License** — free for learning and portfolio sharing.

---

## ✨ Developer Info
**👨‍💻 Ariful Islam**  
**📧** [Your Email Here]  
**🌐** [GitHub Profile or Portfolio Link]  

> This project represents strong analytical capability, advanced Excel modeling, and business intelligence storytelling through data.
