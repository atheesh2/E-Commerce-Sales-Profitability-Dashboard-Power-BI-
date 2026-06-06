# E-Commerce Sales & Profitability Dashboard (Power BI)

A centralized corporate business intelligence dashboard built from scratch using the verbatim **Sample - Superstore.csv** dataset (9,994 transactional rows). This project delivers critical performance visibility, maps regional profitability, and empowers regional managers to make data-driven logistics and sales decisions.

---


## 🚀 Key Features & Achievements

* **Centralized BI Infrastructure:** Extracted, cleaned, and modeled a ~10,000-row global retail dataset, establishing a verified single source of truth for executive reporting.
* **Executive Performance Tracking:** Engineered high-impact KPI summary tiles capturing total business health metrics: **Total Revenue ($2.30M)** and **Total Profit ($286.40K)**.
* **Temporal Trend Analysis:** Created interactive time-series visualizations to analyze monthly and quarterly sales cycles, directly identifying seasonal revenue spikes.
* **Dynamic Parameter Slicing:** Integrated dynamic multi-select parameter filtering (Slicers) allowing regional managers to instantly isolate regional data, transitioning field decisions from intuition to hard insights.
* **Calculated Intelligence:** Designed a suite of DAX measures tracking revenue splits, profit margins, and performance benchmarks for executive-level updates.

---

## 📐 Data Architecture & Schema

To optimize analytical performance, data from **Sample - Superstore.csv** was structured using a robust **Star Schema** dimensional model inside Power BI Desktop:

* **Fact Table:** `Fact_Orders` (Tracks order transactions, quantities, revenue, discounts, and profitability).
* **Dimension Tables:** `Dim_Customer` (Segment, Name), `Dim_Product` (Category, Sub-Category, Product Name), `Dim_Geography` (Country, State, City, Region), and a dedicated `Dim_Date` table generated for comprehensive time-intelligence.

---

## 💾 Core DAX Metrics Showcase

The calculated measures below form the algorithmic backbone of the dashboard's analytics:

### 
1. Total Revenue
```dax
Total Revenue = SUM('Sample - Superstore'[Sales])
2. Total Profit
Code snippet
Total Profit = SUM('Sample - Superstore'[Profit])
3. Profit Margin %
Code snippet
Profit Margin % = DIVIDE([Total Profit], [Total Revenue], 0)
4. Year-over-Year (YoY) Sales Growth
Code snippet
YoY Sales Growth = 
VAR PreviousYearSales = CALCULATE([Total Revenue], SAMEPERIODLASTYEAR('Dim_Date'[Date]))
RETURN 
DIVIDE([Total Revenue] - PreviousYearSales, PreviousYearSales, 0)
