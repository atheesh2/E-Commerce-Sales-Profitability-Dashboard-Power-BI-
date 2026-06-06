#Global Sales Performance & Operations Dashboard Solution (Power BI)

A centralized corporate business intelligence dashboard built from scratch using the verbatim . This project delivers critical performance visibility, maps regional profitability, and empowers regional managers to make data-driven logistics and sales decisions.

---


🚀 Key Features & AchievementsCross-Functional BI Infrastructure: 
Streamlined and modeled multiple relational enterprise data sheets (Assign.xlsx, People.xlsx, Returns.xlsx), consolidating isolated corporate metrics into a single source of truth for global sales and operations. 

Executive Performance Tracking: Engineered clean KPI matrix tiles tracking Total Sales ($2.94M) against a target baseline of $2.89M to monitor top-line corporate health. 

Automated Risk Mitigation: Designed a conditional, dynamic Operational Alert Panel directly in the UI to surface critical business anomalies, instantly flagging localized target deficits (e.g., South Region missing targets by 12%), return surges, and shipping delays.

Advanced Supply Chain Analytics: Programmed complex, optimized DAX equations to monitor key fulfillment risk factors, explicitly calculating Product Return Rate % by Category and Delivery Delay Rate % by Ship Mode.

Granular Personnel & Regional Slicing: Integrated synchronized multi-select slicers mapping performance boundaries for specific regions and Account Managers (Emily Burns, Ross DeVincentis, and Damala Kotsonis) to eliminate reporting latency.  

Geographic & Trend Distributions: Created interactive time-series charts (Sales LY) paired with territory-level horizontal visualizations to instantly map historical performance across high-volume states like England and Île-de-France.

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
