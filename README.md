
/
README_PowerBI_CLEAN.md


Sales Performance Analysis | Power BI
Power BI • Power Query • DAX • Star-schema modelling • KPI reporting

Project overview
This project analyses a synthetic UK retail sales dataset covering 2024, 2025 and January–August 2026. It demonstrates data modelling, DAX measures, KPI reporting and business-focused dashboard design.

Business questions
How are net revenue, gross profit and gross margin changing over time?

Which products, categories, regions and sales channels contribute most to revenue?

How do 2024, 2025 and January–August 2026 compare?

Which areas show the strongest commercial performance?

Data model
Table	Grain	Key
FactSales	One sales line per order item	SalesLineID
DimProducts	One product	ProductID
DimCustomers	One customer	CustomerID
DimDate	One calendar day	Date
The model uses one-to-many relationships from the dimension tables to FactSales.

KPI definitions
Net Revenue: Quantity × Unit Price × (1 − Discount %)

COGS: Quantity × Unit Cost

Gross Profit: Net Revenue − COGS

Gross Margin %: Gross Profit ÷ Net Revenue

Average Order Value: Net Revenue ÷ Completed Orders

Cancelled orders are excluded from revenue calculations.

Key results
Period	Completed orders	Net revenue	Gross profit	Gross margin
2024	523	£228,639	£74,112	32.4%
2025	604	£296,708	£94,009	31.7%
2026 Jan–Aug	430	£189,950	£60,980	32.1%
January–August revenue comparison: 2024 £160,875 · 2025 £183,991 · 2026 £189,950

Dashboard


Key insights
Revenue increased from £228.6k in 2024 to £296.7k in 2025.

January–August revenue increased across all three comparison periods.

Gross margin remained stable at approximately 32%.

The analysis supports comparison by product, category, region, sales channel and time period.

Power BI techniques demonstrated
Power Query data preparation

Star-schema data modelling

Date dimension

DAX measures

Time-based comparisons

KPI cards

Trend analysis

Product and regional performance analysis

Interactive filtering and business reporting

Repository contents
File	Description
PowerBI_Sales_Data.xlsx	Source workbook
FactSales.csv	Sales fact table
DimProducts.csv	Product dimension
DimCustomers.csv	Customer dimension
DAX_Measures.txt	DAX measures
Data_Dictionary.csv	Field definitions
validation_kpis.csv	KPI validation results
PowerBI_Theme.json	Dashboard theme
Build_Dashboard.md	Dashboard specification
dashboard_design_reference.png	Dashboard design
Tools
Power BI Desktop · Power Query · DAX · Excel
