# 📊 Superstore Sales Dashboard — Power BI

> **End-to-end executive analytics solution** built on the Global Superstore dataset — transforming 4 years of raw transactional data (2011–2014) into a fully interactive, single-page Power BI dashboard that delivers instant business intelligence across sales, profit, margin, and regional performance.

<br>

## 🖥️ Dashboard Preview

<img width="1309" height="736" alt="Screenshot 2026-04-22 112832" src="https://github.com/user-attachments/assets/92457aff-d587-472c-8976-39270666c425" />


<br>

---

## 🎯 Project Overview

| | |
|---|---|
| **Tool** | Microsoft Power BI Desktop |
| **Dataset** | Global Superstore (2011–2014) |
| **Rows Analysed** | 9,994 transactions |
| **Date Range** | 01 Jan 2011 — 31 Dec 2014 |
| **Dashboard Pages** | 1 (Single-page executive layout) |
| **Slicers** | Date Range · Segment · Profit Status |
| **Interactivity** | Cross-filtering · Dynamic KPI cards · Drill-through |

<br>

---

## 💡 Business Problem

Retail and e-commerce businesses generate thousands of transactions daily — but raw data alone tells no story. Managers need answers fast:

- **Which regions are driving revenue — and which are underperforming?**
- **Is the business actually profitable after discounts?**
- **Which product categories and individual SKUs contribute the most to the bottom line?**
- **How does profit margin fluctuate across quarters?**

This dashboard answers all of the above in **under 60 seconds** — without opening a single spreadsheet.

<br>

---

## 📈 Key Performance Indicators (Live KPI Cards)

| KPI | Value | Insight |
|---|---|---|
| 💰 **Total Sales** | **$2.30M** | Full 4-year gross revenue across all regions and categories |
| 📦 **Total Profit** | **$286K** | Net profit after all costs — positive across the portfolio |
| 📉 **Profit Margin %** | **12.47%** | Healthy margin; Technology drives it up, Furniture pulls it down |
| 🛒 **Total Orders** | **5,009** | Unique orders placed — calculated using DISTINCTCOUNT on Order ID |

> Each KPI card uses a **branded icon** and **colour-coded border** matching the theme — Blue for Sales, Green for Profit, Orange for Margin, Purple for Orders.

<br>

---

## 🔍 Business Insights Delivered

### 1. 🌍 Sales vs Profit — Regional Analysis
| Region | Total Sales | Total Profit |
|---|---|---|
| West | $0.73M | $0.11M |
| East | $0.68M | $0.09M |
| Central | $0.50M | $0.04M |
| South | $0.39M | $0.05M |

> **Key Finding:** The West region leads in both sales and profit. Central generates significant revenue ($0.50M) but delivers the lowest profit ($0.04M) — indicating high discounting or cost inefficiencies that management should investigate immediately.

---

### 2. 🏆 Top 5 Products by Sales
| Rank | Product | Sales |
|---|---|---|
| 1 | Canon imageCLASS 2200 Advanced Copier | $62K |
| 2 | Fellowes PB500 Electric Punch Plastic Comb... | $27K |
| 3 | Cisco TelePresence System Executive E40 | $23K |
| 4 | HON 5400 Series Task Chairs for Big and Tall | $22K |
| 5 | GBC DocuBind TL300 Electric Binding System | $20K |

> **Key Finding:** Technology products dominate the top 5. The Canon copier alone ($62K) outsells the next product by 2.3× — a clear candidate for promotional investment.

---

### 3. 🏙️ Top 5 Cities by Sales
| Rank | City | Sales |
|---|---|---|
| 1 | New York City | $0.26M |
| 2 | Los Angeles | $0.18M |
| 3 | Seattle | $0.12M |
| 4 | San Francisco | $0.11M |
| 5 | Philadelphia | $0.11M |

> **Key Finding:** New York City contributes 44% more revenue than the second city (Los Angeles). The top 5 cities collectively drive a disproportionate share of total revenue — making them high-priority markets for retention and expansion.

---

### 4. 🍩 Sales by Category — Revenue Share
| Category | Share |
|---|---|
| Technology | 36.4% |
| Furniture | 32.3% |
| Office Supplies | 31.3% |

> **Key Finding:** All three categories contribute nearly equally — but Technology's 36.4% share at a higher profit margin makes it the most valuable category per dollar of revenue. Office Supplies volume is high but margin is thinner.

---

### 5. 📅 Quarterly Profit Margin Trend
| Quarter | Profit Margin % |
|---|---|
| Q1 | 13.05% |
| Q2 | 12.73% |
| Q3 | 11.75% ⚠️ Lowest |
| Q4 | 12.61% |

> **Key Finding:** Q3 is consistently the weakest margin quarter — likely driven by mid-year discount campaigns. Q1 shows the strongest margin, suggesting pricing discipline at the start of the year. This trend should be used to time promotional spend.

<br>

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| **Power BI Desktop** | Dashboard design, data modelling, visualisation |
| **DAX (Data Analysis Expressions)** | All KPI measures — Total Sales, Profit, Margin %, Orders |
| **Power Query (M Language)** | Data cleaning, column standardisation, date table creation |
| **Microsoft Excel (.xlsx)** | Source data format |
| **GitHub** | Version control and portfolio hosting |

<br>

---

## 🧮 DAX Measures — Complete Reference

```dax
-- ── KPI 1: Total Sales ──────────────────────────────────────
Total Sales =
  SUM( Orders[Sales] )

-- ── KPI 2: Total Profit ─────────────────────────────────────
Total Profit =
  SUM( Orders[Profit] )

-- ── KPI 3: Profit Margin % ──────────────────────────────────
Profit Margin % =
  DIVIDE(
    [Total Profit],
    [Total Sales],
    0
  )

-- ── KPI 4: Total Orders (unique) ────────────────────────────
Total Orders =
  DISTINCTCOUNT( Orders[Order ID] )

-- ── YoY Sales Change ────────────────────────────────────────
Sales LY =
  CALCULATE(
    [Total Sales],
    SAMEPERIODLASTYEAR( DateTable[Date] )
  )

Sales YoY % =
  DIVIDE(
    [Total Sales] - [Sales LY],
    [Sales LY],
    0
  )

-- ── Category Share % (for donut chart) ──────────────────────
Sales % of Total =
  DIVIDE(
    [Total Sales],
    CALCULATE( [Total Sales], ALL( Orders[Category] ) ),
    0
  )

-- ── Quarterly Profit Margin ──────────────────────────────────
Quarterly Margin % =
  DIVIDE(
    CALCULATE( [Total Profit] ),
    CALCULATE( [Total Sales] ),
    0
  )
```

<br>

---

## 🎨 Dashboard Design System

| Element | Specification |
|---|---|
| **Background** | `#1B2A4A` Navy (header) · `#F0F4F8` Light grey (canvas) |
| **Sales KPI colour** | `#1565C0` Royal Blue |
| **Profit KPI colour** | `#2E7D32` Forest Green |
| **Margin KPI colour** | `#E65100` Burnt Orange |
| **Orders KPI colour** | `#6A1B9A` Deep Purple |
| **Font** | Segoe UI (Power BI default) |
| **Chart style** | Flat, no gradients, white card backgrounds |
| **Slicers** | Date range slider · Dropdown segment · Dropdown profit status |

<br>

---

## 📐 Dashboard Layout — Visual Inventory

```
┌──────────────────────────────────────────────────────────────────┐
│  HEADER — Title · Date Slicer · Segment Slicer · Profit Status   │
├──────────┬──────────┬──────────┬──────────────────────────────────┤
│ KPI:     │ KPI:     │ KPI:     │ KPI:                             │
│ $2.30M   │ $286K    │ 12.47%   │ 5009 Orders                      │
│ Sales    │ Profit   │ Margin % │                                  │
├──────────┴──────────┼──────────┴────────────┬─────────────────────┤
│ Sales vs Profit     │ Top 5 Products        │ Top 5 Cities        │
│ (Clustered Bar)     │ (Column Chart)        │ (Horizontal Bar)    │
├─────────────────────┼───────────────────────┤                     │
│ Quarterly Margin    │ Sales by Category     │                     │
│ (Area/Line Chart)   │ (Donut Chart)         │                     │
└─────────────────────┴───────────────────────┴─────────────────────┘
```

<br>

---

## 🗂️ Repository Structure

```
superstore-sales-powerbi/
│
├── 📄 README.md                          ← You are here
├── 📊 Superstore_Sales_Dashboard.pbix    ← Power BI dashboard file
├── 📁 data/
│   └── 📄 Superstore_Sales_Data.xlsx    ← Raw source dataset
├── 📁 assets/
│   ├── 🖼️ dashboard_screenshot.png      ← Full dashboard preview
│   └── 🖼️ kpi_icons/                   ← Custom SVG icons used
│       ├── icon_sales.svg
│       ├── icon_profit.svg
│       ├── icon_margin.svg
│       └── icon_orders.svg
└── 📁 dax/
    └── 📄 all_measures.dax              ← All DAX formulas exported
```

<br>

---

## 💼 What This Project Demonstrates

| Skill | Evidence in Dashboard |
|---|---|
| **DAX Mastery** | 8 custom measures including DIVIDE, DISTINCTCOUNT, SAMEPERIODLASTYEAR, ALL |
| **Data Modelling** | Date table created and marked, relationships built in Model view |
| **Data Cleaning** | Power Query used to standardise columns, handle nulls, parse dates |
| **Business Acumen** | Insights framed as business decisions, not just numbers |
| **Visual Design** | Colour-coded by KPI type, consistent spacing, no chart junk |
| **Storytelling** | Dashboard tells the profit story from total → region → product → city |
| **Interactivity** | Cross-filtering across all 7 visuals, date range slider, 2 dropdown slicers |

<br>

---

> 🔗 Full project with .pbix file and all DAX measures on GitHub → [link in bio]
>
> #PowerBI #DataAnalytics #DataAnalyst #DAX #BusinessIntelligence #Dashboard #DataVisualization #SuperstoreSales #SQL #Excel #Portfolio #DataScience #CareerGrowth #IndiaDataCommunity

<br>

---

## 📬 Connect With Me

| Platform | Link |
|---|---|
| 🔗 LinkedIn | [linkedin.com/in/dataanalyst-manish](https://www.linkedin.com/in/dataanalyst-manish) |
| 💻 GitHub | [github.com/bisht5431-source](https://github.com/bisht5431-source) |
| 📧 Email | alphainsights123@gmail.com |

<br>

---

<div align="center">

**⭐ If this project helped you, please star the repository — it helps other analysts find it too.**

*Built by Manish Bisht — Data Analyst · SQL · Power BI · Excel · Python*

</div>
