# Build the dashboard in Power BI Desktop

**Expected effort:** This is a build kit, not a finished `.pbix` file. Build or upload your existing matching `.pbix` before calling your GitHub portfolio finished.

## 1. Import the data
- Download and extract the ZIP to a permanent folder.
- Power BI Desktop > Home > Get data > Excel workbook > `PowerBI_Sales_Data.xlsx`.
- Select `FactSales`, `DimProducts` and `DimCustomers` sheets; choose Transform Data.
- If Excel import struggles, import the three corresponding CSVs instead (Home > Text/CSV).
- In Power Query set `FactSales[OrderDate]` and `DimCustomers[SignupDate]` to **Date**, IDs and Quantity to **Whole number**, Price/Cost/Discount to **Decimal number**. Use the correct locale for ISO YYYY-MM-DD dates. Do not sum IDs.
- Close & Apply.

## 2. Build the star schema
- In Model view, link `DimProducts[ProductID]` (one) to `FactSales[ProductID]` (many).
- Link `DimCustomers[CustomerID]` (one) to `FactSales[CustomerID]` (many).
- Modeling > New table: paste the `DimDate = ADDCOLUMNS(...)` block from `DAX_Measures.txt`.
- Link `DimDate[Date]` (one) to `FactSales[OrderDate]` (many).
- Use **single-direction** filtering from dimensions to fact. Avoid bidirectional unless justified.
- Mark DimDate as Date table and sort DimDate[Month] by DimDate[Month No].

## 3. Create measures
- Modeling > New measure. Paste each named DAX measure from `DAX_Measures.txt` **one at a time**.
- Format currency measures GBP, Gross Margin/YoY/Cancellation as percent (1 decimal), and counts whole numbers.
- Check the totals against `validation_kpis.csv` (no filter for all-time values; use Year slicer to check each year).

## 4. Design Page 1: Executive Overview
- Canvas 16:9, white/off-white background, theme `PowerBI_Theme.json` (View > Themes > Browse for themes).
- Top: title **Sales Performance | 2024–Aug 2026** and a small **Synthetic dataset** subtitle.
- Slicers: Year, Region, Category, Sales Channel. Use dropdowns or a compact horizontal row.
- 5 KPI cards: Net Revenue, Gross Profit, Gross Margin %, Completed Orders, Average Order Value.
- Line chart: DimDate[YearMonth] vs Net Revenue (chronological order).
- Clustered bar: DimProducts[Category] vs Net Revenue.
- Horizontal bar: DimProducts[ProductName] vs Net Revenue (Top 6).
- Column/bar: DimCustomers[Region] vs Net Revenue.
- Donut: FactSales[SalesChannel] vs Net Revenue.
- Check slicer interaction and hover tooltips. If using the Year slicer, explain 2026 is Jan-Aug only.

## 5. Design Page 2: Product & Customer Detail
- Matrix Product Category > Product Name, measures Revenue, Units Sold, Gross Profit, Gross Margin %.
- Matrix Region > City, measures Revenue, Completed Orders, Average Order Value.
- Add Customer Segment slicer and a monthly chart. Optional drillthrough by product name.

## 6. Verify and publish
- Verify data types and relationships; compare annual figures with `validation_kpis.csv`.
- Demonstrate selecting Region and Category: every visual should respond as intended.
- Save **Sales_Performance_Dashboard.pbix** to this project folder.
- Export/screenshoot pages as `dashboard_overview.png` and `product_customer_detail.png`.
- Upload the `.pbix`, both screenshots, README, Excel data, CSVs, DAX, theme and documentation.
- If your `.pbix` is too large for browser upload, GitHub's per-file browser limit applies; use Git LFS or omit the PBIX and explain why. Do not claim the PBIX is supplied if it is not.

## 7. Business interpretation
- Use same-month windows for partial-year comparisons. Jan-Aug 2026 cannot be compared fairly with Jan-Dec 2025.
- Gross profit excludes shipping, returns, salaries, tax and overhead; do not describe it as net profit.
- Synthetic trends are illustrative, not evidence about a real retailer.
