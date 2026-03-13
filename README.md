# 📊 Blinkit Analytics Dashboard — Power BI

> End-to-end Business Intelligence project built on raw Blinkit operational data — covering marketing performance, customer analytics, delivery metrics, and revenue forecasting across four interactive report pages.

---

## 🧭 Project Overview

This dashboard simulates a real-world analytics workflow for **Blinkit**, India's instant grocery delivery platform. Starting from 11 publicly available raw CSV files, the project covers the full BI pipeline:

- **Ingestion & Transformation** — Power Query (M language)
- **Data Modelling** — Star schema with Calendar table & relationships
- **Business Logic** — DAX measure groups per domain
- **Visualisation** — Four polished, interactive report pages

| Metric | Value |
|---|---|
| Raw rows processed | ~30,000 |
| Source files | 11 CSV files |
| Dashboard pages | 4 |
| Data model tables | 17 (facts, dims, measures, calendar) |
| Time period covered | 2023 – 2024 |

---

## 📁 Repository Structure

```
├── data/
│   ├── blinkit_orders.csv
│   ├── blinkit_customers.csv
│   ├── blinkit_order_items.csv
│   ├── blinkit_products.csv
│   ├── blinkit_delivery_performance.csv
│   ├── blinkit_customer_feedback.csv
│   ├── blinkit_marketing_performance.csv
│   ├── blinkit_inventory.csv
│   ├── blinkit_inventoryNew.csv
│   ├── Category_Icons.xlsx
│   └── Rating_Icon.xlsx
├── Blinnkit_group_5.pbix         # Power BI report file
└── README.md
```

---

## 📊 Dashboard Pages

### Page 1 — Intro / Landing
Branded landing page with Blinkit logo, project title, and navigation buttons to all report sections.

### Page 2 — Marketing Performance
Tracks campaign ROI, ad spend, and conversion funnel across channels and audience segments.

| Visual | Purpose |
|---|---|
| ROAS Gauge | Actual vs configurable target ROAS |
| Revenue vs Spend Gauge | High-level spend efficiency |
| KPI Cards ×4 | Impressions, Clicks, Conversions, # Campaigns |
| Combo Chart (Line + Column) | Monthly Spend & Revenue trend |
| Donut Chart | Channel distribution |
| Decomposition Tree | Conversion breakdown by channel → audience → time |
| Slicers ×4 | Channel, Year, Quarter, Target Audience |

### Page 3 — Customer Analytics
360° view of customer health, segmentation, geography, and product preferences.

| Visual | Purpose |
|---|---|
| KPI Cards ×5 | Total Sales, Orders, AOV, Customer Sat %, On-Time % |
| Clustered Column Chart | Sales by customer segment |
| Filled Map | Orders and AOV distribution by area |
| Donut Chart | Sales by product category |
| Bar Chart | Rating distribution from feedback |
| Bar Chart | Top products by quantity sold |
| Slicers ×4 | Year, Quarter, Area, Category |

### Page 4 — Forecasting
Forward-looking projections using Power BI's native time-series forecasting.

- **Marketing Revenue Forecast** — projected campaign revenue
- **Order Revenue Forecast** — total order revenue trend
- **Campaign Conversions Forecast** — conversion volume outlook

---

## 🗄️ Data Model

Star schema design with **17 tables** across four categories:

**Fact Tables** (raw sources)
- `blinkit_orders`, `blinkit_order_items`, `blinkit_delivery_performance`
- `blinkit_marketing_performance`, `blinkit_customer_feedback`
- `blinkit_inventory`, `blinkit_inventoryNew`

**Dimension Tables**
- `blinkit_customers`, `blinkit_products`

**Merged/Analytical Views** (created in Power Query)
- `orders_extended` — orders joined with customer data
- `order_items_extended` — order items joined with product info
- `inventory` — consolidated inventory (append of both inventory files)

**Calculated Tables** (DAX)
- `Calendar` — auto-generated date table for time intelligence
- `Marketing Measures`, `Customer Measures`, `Forecasting Measures` — measure isolation tables
- `Target ROAS`, `Parameter` — What-If parameter tables

---

## 🧮 Key DAX Measures

| Measure | Table | Description |
|---|---|---|
| `ROAS` | Marketing | Revenue ÷ Spend — shown on gauge vs target |
| `Total Revenue` | Marketing | Sum of campaign revenue |
| `Total Spend` | Marketing | Sum of campaign ad spend |
| `Total Impressions` | Marketing | Top-of-funnel reach |
| `Total Clicks` | Marketing | Mid-funnel engagement |
| `Total Conversions` | Marketing | Bottom-funnel actions |
| `Number of Campaigns` | Marketing | Distinct campaign count |
| `Total Sales` | Customer | Sum of order totals |
| `Total Orders` | Customer | Count of distinct orders |
| `AOV` | Customer | Average Order Value |
| `Customer Sat %` | Customer | % of high-rated feedback (4–5★) |
| `OnTime %` | Customer | % of on-time deliveries |
| `Target ROAS Value` | Parameter | User-adjustable ROAS benchmark |

---

## ⚙️ Power Query Transformations

1. **Data Type Enforcement** — Corrected types for all date, numeric, and text columns across all 11 files
2. **Column Cleaning & Renaming** — Standardised names, trimmed whitespace, removed duplicates
3. **Null Handling** — Managed nulls in delay reasons, feedback text, and foreign key fields
4. **Merge: `orders_extended`** — Left join of orders + customers for segment/area-enriched order data
5. **Merge: `order_items_extended`** — Join of order items + products for category-level analysis
6. **Inventory Consolidation** — Append of two inventory files into a single unified table
7. **Date Extraction** — Isolated date-only columns from datetime fields for Calendar table relationships

---

## 🎨 Custom Visuals Used

| Visual | Use |
|---|---|
| Chiclet Slicer | Styled tile-based slicers for filters |
| Map by Squillion | Enhanced geographic mapping |
| Performance Bubble Chart | Multi-metric campaign scatter |
| Custom Donut / Pie | Enhanced donut with better labelling |
| Word Cloud | Feedback text exploration |

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| **Power BI Desktop** | Report authoring, visual design, publishing |
| **Power Query (M)** | Data ingestion, cleaning, transformation, merging |
| **DAX** | Business logic, KPIs, time intelligence, What-If |
| **Star Schema Design** | Relational data modelling |
| **Power BI Forecasting** | Native time-series projection |
| **What-If Parameters** | Interactive target-setting in reports |

---

## 📌 Key Learnings

- Designing an end-to-end BI pipeline from raw, unstructured public data
- Building a normalised star schema with proper relationship management
- Authoring modular DAX measures isolated in dedicated measure tables
- Using Power Query M to create enriched analytical views via merge/append
- Implementing What-If parameters for dynamic, user-controlled analysis
- Applying Power BI's native forecasting for business projection use cases

---

*Academic class project · Data Analytics · Power BI · 2024–25*
