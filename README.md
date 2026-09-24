# FUTURE_DS_01
# 📊 Sample Superstore Executive Performance Dashboard 
## 📌 Project Overview
An executive-level, interactive business intelligence dashboard built in **Power BI** utilizing the classic **Sample - Superstore dataset**.  
This project transforms raw retail data into actionable insights, tracking **revenue, profitability, customer behavior, and regional performance**.
It is designed to provide executives and decision-makers with **real-time, interactive insights** into retail performance across multiple dimensions.

---

## 📊 Dataset

**Dataset:** Sample - Superstore  - Dirty Data for Cleaning Training  
**Source:** Kaggle
**Period:** 2014–2017
**Rows:** 9,995
**Columns:** 21
**Data type:** Raw, uncleaned transaction data
### 📊 Dataset Metadata
- **Row ID** → Unique ID for each row  
- **Order ID** → Unique Order ID per customer  
- **Order Date / Ship Date** → Timeline of purchase and delivery  
- **Ship Mode** → Customer‑specified shipping method  
- **Customer ID / Name** → Unique identifiers for customers  
- **Segment** → Customer segment (Consumer, Corporate, Home Office)  
- **Country / City / State / Postal Code / Region** → Geographic attributes  
- **Product ID / Name / Category / Sub‑Category** → Product details  
- **Sales** → Revenue generated  
- **Quantity** → Units sold  
- **Discount** → Discount applied  
- **Profit** → Net profit or loss
  
### 🎯 Objectives
- Transform raw retail data into **actionable insights**.
- Enable **data-driven decision-making** through interactive visuals.
- Highlight **profitability, customer behavior, and regional performance**.
- Identify **strategic opportunities and risks** within product categories and markets.

### 🔍 Scope
- Covers sales transactions from **2014–2017**.  
- Includes analysis of **Revenue, Profit, Orders, Quantity, and Customer Segments**.  
- Provides **regional and category-level breakdowns** for deeper insights.  

### 🏆 Value Proposition
- **Executives** gain a high-level view of KPIs with drill-down capabilities.  
- **Analysts** can explore trends, seasonality, and profitability drivers.  
- **Business teams** can identify unprofitable discounts, low-margin categories, and top-performing regions/customers.  

This project demonstrates how **Power BI, Power Query, and DAX** can be leveraged to build a scalable, professional-grade dashboard that supports **strategic retail management**.


## 🖼️ Dashboard Preview
![DASHBOARD PREVIEW](https://github.com/Malayasis-Banerjee/FUTURE_DS_01/blob/main/Screenshot%202026-09-24%20002637.png)

---

## 🚀 Key Features & Layout Architecture

The dashboard follows a clean, structured executive layout (**16:9 widescreen**) designed for rapid decision-making:

### Top KPI Summary Cards
- **Total Profit:** $286.40K (with conditional coloring)  
- **Total Orders:** 5K transactions  
- **Total Quantity:** 38K units sold  
- **Total Revenue:** $2.30M  

### Global Interactive Slicers
- Filter instantly by **Category, Region, Sub-Category**, and **Order Date Range (2014–2017)**.

### Core Analytical Visuals
- **Total Revenue by Segment:** Donut chart breakdown (Consumer, Corporate, Home Office).  
- **Revenue & Profit by Sub-Category:** Combo chart highlighting product performance and margins.  
- **Profit by City:** Horizontal bar chart (e.g., New York City, Los Angeles, Seattle).  
- **Customer Performance:** Top customers ranked by revenue and profitability.  
- **Category Profitability:** Bar chart comparing Technology, Office Supplies, and Furniture.  
- **Monthly Revenue Trend:** Area/Line chart showing seasonality and annual velocity.  
- **Regional Profitability:** Bar chart comparing West, East, Central, and South regions.  

---

## 🛠️ Data Cleaning & ETL Steps (Power Query)

Before building the data model and visualizations, the raw dataset underwent rigorous preparation in **Power Query Editor**:

- **Promoted Headers & Data Typing:** Correct data types (Dates, Currency, Text, Integers).  
- **Error-Free Date Transformations:** Reconstructed clean date columns using custom Power Query M code:

```m
// Step 1: Split date column by delimiter
= Table.SplitColumn(
    #"Extracted Values1",
    "Ship Date",
    Splitter.SplitTextByDelimiter("/", QuoteStyle.Csv),
    {"Day","Month","Year"}
)

// Step 2: Reconstruct clean date using #date
= Table.AddColumn(
    #"Removed Columns1",
    "Shiped Date",
    each #date([Year1], [Month1], [Day1]),
    type date
)
```

_ _ _
## 📈 DAX Measures Used
```m
// Total Revenue (Sales)
Total Revenue = SUM('Superstore'[Sales])

// Total Profit
Total Profit = SUM('Superstore'[Profit])

// Profit Margin
Profit Margin = DIVIDE([Total Profit], [Total Revenue], 0)

// Total Orders
Total Orders = DISTINCTCOUNT('Superstore'[Order ID])
```

## 💡 Key Learnings & Strategic Insights

- **The Discount Trap**  
  Discounts exceeding **20%** often eliminate net profit margins, turning high‑volume transactions into losses.  
  👉 Recommendation: Enforce stricter discounting rules to protect profitability.

- **Category Profit Paradox**  
  Furniture generates substantial gross revenue but delivers **low net profitability** compared to Technology and Office Supplies.  
  👉 Cause: High warehousing, handling, and shipping overhead.

- **Geographic Imbalances**  
  The **West and East regions** are strong drivers of profitability, while the **Central and South regions** face margin compression due to unprofitable product lines.  
  👉 Insight: Regional product strategy adjustments are needed.

- **Q4 Holiday Seasonality**  
  Sales consistently spike from **October through December**, highlighting predictable seasonal demand.  
  👉 Action: Prioritize early inventory staging and optimize staffing for holiday periods.

## ⚙️ How to View and Run Locally

### Prerequisites
- Install **Microsoft Power BI Desktop** on your system.

### Steps
1. **Clone the Repository**
   ```bash
    https://github.com/Malayasis-Banerjee/FUTURE_DS_01/blob/main/Future%20Intern%201.pbix
  ```


## 👤 Author

**Malayasis Banerjee**  

Data Analyst Intern | Aspiring Data Analyst
#DataAnalytics #ExploratoryDataAnalysis #SWYNEXTechnologies
