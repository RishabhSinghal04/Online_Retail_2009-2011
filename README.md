# Online Retail 2009-2011

## Table of Contents
- [Introduction](#Introduction)
- [Problem Statement](#Problem-Statement)
- [Dataset](#Dataset)
- [Data Cleaning and Preparation](#Data-Cleaning-and-Preparation)
- [Data Model](#Data-Model)
- [Report Overview](#Report-Overview)
- [Results](#Results)
- [Key Features](#Key-Features)
- [Tools & Technologies](#Tools-and-Technologies)
- [File Structure](#File-Structure)
- [Getting Started](#Getting-Started)


## Introduction

This project presents an interactive **Power BI dashboard** built on the **“Online Retail II” dataset** from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Online+Retail+II). It analyzes **1,067,371 transactions** from a **UK‑based online retailer** between **Dec 2009 and Dec 2011**.  

Combining data quality checks with multi‑page visual reports, it delivers insights into **sales trends**, **product performance**, and **regional revenue patterns**, enabling informed, data‑driven decisions.

![Report Pages](images/report_pages.png)


## Problem Statement

The goal is to transform raw transaction logs into a clean, interactive reporting tool that enables:
- Year-over-Year performance tracking  
- Regional and product hierarchy analysis  
- Identification of top customers and SKUs  
- Detailed drill-through to transaction lines  
- Data-driven decisions on inventory, and customer retention


## Dataset

- Source: **“Online Retail II” dataset** from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Online+Retail+II)
- Span: Dec 1, 2009 – Dec 9, 2011  
- Records: 1,067,371 invoice lines  
- Key fields: InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, Country


## Data Cleaning and Preparation

- Filled blank descriptions using Power Query
- Merged two sheets (2009–2010, 2010–2011) into a single Transactions table  
- Filtered returns (negative Quantity and negative Price) and cancellations (InvoiceNo starts with “C”) 
- Handled missing CustomerIDs and blank Descriptions (flagged or removed)  
- Standardized Country/Region names 

![Report_Page_1](images/issues/Issues_Log.png)


## Data Model

- Star schema: Year_2009_2011 fact table joined to a Date dimension table
- Marked Dim_Date for time intelligence (YoY, rolling windows)
- Relationship: Dim_Date[Date] → Year_2009_2011[InvoiceDate]


## Report Overview

An interactive Power BI report covering the period from December 2009 to December 2011, organized across four pages to deliver layered insights and seamless exploration.


### **Page 1 – Executive Summary**

![Report Page 1](images/report/executive_summary.png)

This page provides a comprehensive view of business performance through a series of high‑impact visual insights:  
- High‑level KPI cards showcase **Total Revenue, Total Quantity, Invoice Count, Average Order Value (AOV)**, and **Average Unit Price (AUP)** for a quick performance snapshot.  
- A **Total Revenue by Year and Month** trend chart outlines historical patterns, supported by revenue forecasts for the next 12 months to aid strategic planning.  
- **Top 5 Customers** and **Top 5 SKUs** are highlighted in bar charts, revealing the most valuable relationships and product lines.  
- **Regional revenue distribution** offers a clear breakdown of contributions by key markets, pinpointing areas of strength and growth opportunity.  


### **Page 2 – Revenue 2010 vs 2011**

![Report Page 2](images/report/revenue_2010_vs_2011.png)

This page delivers a clear comparative view of business shifts between 2010 and 2011, spotlighting performance drivers and market dynamics.
- **Revenue change analysis** captures both the **overall year‑on‑year delta** and **month‑by‑month variations**, revealing periods of **growth** and **decline** across the calendar year.  
- **Customer segmentation insights** contrast **recurring** and **new customer counts**, highlighting **acquisition trends** and **retention performance** in **2011**.  
- **Volume versus invoicing patterns** compare **total quantities sold** with **invoice volumes**, offering a lens on **transaction size** and **sales frequency** changes.  
- **SKU‑level revenue composition** examines shifts in the mix between **key product codes**, providing visibility into **evolving product demand** and **contribution**.   


### **Page 3 – Regional Revenue Trends**

![Report Page 3](images/report/regional_revenue_trends.png)

This page empowers layered, drill‑down analysis through intuitive, cascading filters and a clear flow of information.
- **Dynamic slicers** for **Year**, **Quarter**, **Month**, and **Day**, along with a convenient **clear‑all control**, allow for flexible, targeted data exploration.
- **Stepwise revenue decomposition** flows from **total revenue** into **regional performance**, then narrows further by **time period** down to the **daily level**, enabling precise identification of trends and anomalies.


### **Page 4 – Geographic Revenue Split**

![Report Page 4](images/report/geographic_revenue_split.png)

**This page visualizes geographic revenue distribution using complementary mapping techniques.**  
- **Bubble Map** displays each location’s revenue as **proportionally sized bubbles**, providing immediate visual cues to relative market scale across regions.  
- **Tree Map** summarizes **regional revenue shares** in a hierarchical layout, enabling quick comparison of contributions from individual countries and markets.


## Results

The Power BI dashboard uncovered several key insights from the Online Retail II dataset (Dec 2009 – Dec 2011):

- **Revenue Decline:**  
  Total revenue in **2011** fell by **£76.10K** compared to 2010. The sharpest decline occurred in **December 2011**, with a drop of nearly **£240K**, based on figures available up to **December 9, 2011**.

- **Seasonality & Trends:**  
  Sales consistently peaked in **November**, driven by pre‑holiday demand. Revenue typically dipped in **January**, reflecting post‑holiday slowdowns.  
  Notably, **November 2011** outperformed the previous year, with revenue rising from **£1.47M in 2010** to **£1.51M in 2011** — an increase of **2.67%**.

- **Regional Performance:**  
  The **United Kingdom** remained the dominant market, generating **£17.9M** in total revenue. However, the strongest **year‑over‑year growth** came from **Australia**, signaling emerging market potential.

- **Regional Revenue Growth**
  - **Australia:** Revenue surged from **£31,792.85** in 2010 to **£137,488.46** in 2011 — an increase of **332.37%**  
  - **France:** Revenue increased from **£146,980.22** in 2010 to **£200,116.80** in 2011 — an increase of **35.99%**

- **Regional Revenue Decline**
  - **United Kingdom:** Dropped from **£8,500,519.91** in 2010 to **£8,276,953.10** in 2011 — a decrease of **2.63%**  
  - **Ireland:** Dropped from **£366,160.86** in 2010 to **£273,420.70** in 2011 — a decrease of **25.29%**

- **Product Performance:**  
  **Stock Code "22423"** generated the highest revenue — **£344,563.25** — despite a relatively low quantity sold (**27,594 units**), indicating strong unit pricing and demand.

These findings highlight shifting regional dynamics, seasonal buying patterns, and high‑value product performance — offering clear direction for inventory planning, market targeting, and strategic decision‑making.

## Key Features

- High-level KPI cards summarizing Total Revenue, Quantity Sold, Invoice Count, Average Order Value, Average Unit Price and YoY Revenue Growth   
- Year-over-Year delta calculations for total and monthly revenue, alongside recurring vs new customer growth
- A revenue‐delta KPI card comparing total 2011 vs 2010 performance
- Monthly variance chart outlining revenue gains and losses by month
- Customer segmentation cards showing recurring and new customers in 2011
- SKU-level revenue mix comparison to highlight shifts in product performance  
- Cascading slicers (Year, Quarter, Month, Day) with a clear-all button for precise drill-down  
- Flowchart-style revenue decomposition from region through year, quarter, month to day granularity  
- Bubble Map displaying each location’s revenue as proportional-sized bubbles
- Treemap view for at-a-glance regional revenue shares  

## Tools and Technologies

- Power BI Desktop (Data preparation: Power Query, visuals & measures: DAX)
- Microsoft Excel 2021: create an issue log to track dataset anomalies, and use Power Query to auto-fill blank descriptions.

## File Structure

```
├── data/
│   ├── online_retail_II.xlsx
│   ├── Filled_Blank_Desc.xlsx
│   └── Issues_Log.xlsx
├── images/
│   ├── dashboard/
│   │   ├── executive_summary.png
│   │   ├── revenue_2010_vs_2011.png
│   │   └── regional_revenue_trends.png
│   │   └── map.png
│   └── issues/
│       └── Issues_Log.png
├── pbix/
│   └── Online_Retail.pbix
└── README.md
```

## Getting Started

1. Clone the repo and open the `.pbix` file in Power BI Desktop.  
2. Point the source in Power Query to `data/Filled_Blank_Desc.xlsx`.  
3. Refresh to load and transform.  
4. Explore the dashboard pages, slicers, and drill-through details.