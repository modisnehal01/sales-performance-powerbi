# Sales Performance Dashboard | Power BI Portfolio 01

**Power BI • Power Query • DAX • Star-schema modelling • Executive reporting**

An end-to-end **synthetic UK retail sales** dashboard build kit covering **2024, 2025 and January–August 2026**. This project demonstrates business KPI design, multi-table modelling, interactive reporting and commercially useful interpretation. It does **not** represent paid employment or real client outcomes.

> **Portfolio status:** This repository contains the data, validated KPI benchmarks, DAX, theme, build instructions and an **illustrative layout mockup**. 

## Business questions

- What are net revenue, gross profit, gross margin, completed orders and average order value?
- How do product categories, individual products, regions and sales channels contribute to revenue?
- How do 2024, 2025 and **2026 Jan–Aug** compare on the *same-period* basis?
- Which segments deserve investigation and what data limitations affect the interpretation?

## Data model

| Table | Grain | Key |
|---|---|---|
| `FactSales` | One line item within an order | `SalesLineID` |
| `DimProducts` | One product | `ProductID` |
| `DimCustomers` | One customer | `CustomerID` |
| `DimDate` (DAX) | One calendar day | `Date` |

`DimProducts`, `DimCustomers` and `DimDate` have one-to-many, single-direction relationships to `FactSales`. There are **2,713 order lines, 1,607 orders, 12 products and 65 fictitious customers**. Completed-order sales count toward revenue; cancelled orders are excluded.

**Revenue =** `Quantity × UnitPriceGBP × (1 − DiscountPct)` for completed orders. **COGS =** `Quantity × UnitCostGBP` for completed orders. **Gross profit =** revenue − COGS. This is gross profit before shipping, returns, tax and operating costs.

## Validated synthetic-data KPIs

| Order period | Completed orders | Net revenue | Gross profit | Gross margin |
|---|---:|---:|---:|---:|
| 2024 | 523 | £228,639 | £74,112 | 32.4% |
| 2025 | 604 | £296,708 | £94,009 | 31.7% |
| 2026 | 430 | £189,950 | £60,980 | 32.1% |

**Like-for-like revenue, January–August only:** 2024 £160,875; 2025 £183,991; 2026 £189,950. Do not compare 2026's eight months with a complete prior calendar year.

## Dashboard design reference
[Illustrative dashboard layout, Power BI screenshot](dashboard_design_reference.png) dashboard_design_reference.png



## Repository files

| File | Purpose |
|---|---|
| [PowerBI_Sales_Data.xlsx](PowerBI_Sales_Data.xlsx) | One Excel source workbook, FactSales + two dimensions |
| [FactSales.csv](FactSales.csv) / [DimProducts.csv](DimProducts.csv) / [DimCustomers.csv](DimCustomers.csv) | Separate CSV source files |
| [DAX_Measures.txt](DAX_Measures.txt) | 
| [Build_Dashboard.md](Build_Dashboard.md) | 
| [PowerBI_Theme.json](PowerBI_Theme.json) 
| [Data_Dictionary.csv](Data_Dictionary.csv) |
| [validation_kpis.csv](validation_kpis.csv) | 
| [dashboard_design_reference.png](dashboard_design_reference.png) |

