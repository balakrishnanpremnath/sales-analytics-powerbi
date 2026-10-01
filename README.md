# Sales Analytics Dashboard | Power BI

An interactive Power BI report for exploring sales, profitability,
product performance, customer segments, and regional trends.

Built using Power Query, DAX measures, KPI cards, interactive slicers,
and three connected report pages.

## Dashboard Preview

![Executive Overview](screenshots/01_Executive_Overview.png)

## Project Objective

Sales totals alone do not explain which products, customers, or regions
contribute most to business performance.

This dashboard brings these views together to help users:

- Monitor sales and profit.
- Compare product revenue and profitability.
- Explore customer and regional performance.
- Identify changes in monthly sales.
- Filter results by year, category, province, and customer segment.

## Dashboard KPIs

The documented dashboard snapshot reports:

| KPI | Displayed Value |
|---|---:|
| Total Sales | LKR 115.80M |
| Total Profit | LKR 27.08M |
| Profit Margin | 23.39% |
| Total Orders | Approximately 3K |
| Units Sold | Approximately 8K |
| Total Customers | 349 |
| Average Sales per Customer | LKR 331.81K |

Values reflect the report's data and filter context. Figures displayed
in thousands or millions are rounded.

These are amounts represented in the dataset, not business improvements
attributed to building the dashboard.

## Report Pages

### 1. Executive Overview

Provides an overall view of sales and profitability.

**Includes:**

- Total sales, profit, orders, units sold, and profit margin
- Monthly sales trend
- Sales by province and category
- Top 10 customers and products by sales
- Year, province, and category slicers

### 2. Product Analysis

![Product Analysis](screenshots/02_Product_Analysis.png)

Explores how products contribute to sales and profit.

**Includes:**

- Top 10 products by sales
- Top 10 products by profit
- Sales by category
- Sales-versus-profit comparison
- Category and year slicers

This page supports comparisons between products with high sales
and those with high profit.

### 3. Customer & Regional Analysis

![Customer and Regional Analysis](screenshots/03_Customer_Regional_Analysis.png)

Explores customer contributions and geographic sales patterns.

**Includes:**

- Customer count and average sales per customer
- Top 10 customers by sales
- Sales by customer segment
- Sales by province and city
- Year, province, and customer-segment slicers

## Interpreting the Results

- **Profit margin:** The displayed 23.39% means approximately
  LKR 23.39 of recorded profit per LKR 100 of sales, within the
  same filter context. Its accounting meaning depends on how the
  source dataset defines profit.
- **Average sales per customer:** LKR 331.81K represents total
  sales divided by distinct customers in the selected context.
  It is not average order value or customer lifetime value.
- **Product comparisons:** Sales and profit rankings answer
  different questions. Review both when assessing product performance.

The dashboard supports descriptive analysis. It does not establish
the causes of sales changes or predict future performance.

## Tools and Technologies

| Tool | Purpose |
|---|---|
| Power BI Desktop | Report development and interactive visualization |
| Power Query | Data preparation and transformation |
| DAX | KPI calculations and measures |
| Git and GitHub | Version control and project documentation |

## DAX Measures

The documented measures use the `Raw_Sales_Data` table.

### Total Sales

```DAX
Total Sales =
SUM(Raw_Sales_Data[Sales (LKR)])
```

### Total Profit

```DAX
Total Profit =
SUM(Raw_Sales_Data[Profit (LKR)])
```

### Total Orders

```DAX
Total Orders =
DISTINCTCOUNT(Raw_Sales_Data[Order ID])
```

Distinct order IDs are counted rather than assuming every data row
represents a separate order.

### Units Sold

```DAX
Units Sold =
SUM(Raw_Sales_Data[Quantity])
```

### Profit Margin

```DAX
Profit Margin =
DIVIDE([Total Profit], [Total Sales], 0)
```

This calculates the ratio of total profit to total sales in the
current filter context. Format the measure as a percentage.

### Total Customers

```DAX
Total Customers =
DISTINCTCOUNT(Raw_Sales_Data[Customer ID])
```

### Average Sales per Customer

```DAX
Average Sales per Customer =
DIVIDE([Total Sales], [Total Customers], 0)
```

## Repository Guide

| Path | Contents |
|---|---|
| `dashboard/Sales_Analytics_Dashboard.pbix` | Power BI report |
| `screenshots/01_Executive_Overview.png` | Executive overview preview |
| `screenshots/02_Product_Analysis.png` | Product analysis preview |
| `screenshots/03_Customer_Regional_Analysis.png` | Customer and regional preview |
| `data/` | Location reserved for supporting data files |
| `README.md` | Project overview and usage instructions |

## How to Explore the Report

### 1. Download the Repository

Download the repository ZIP, or clone it:

```bash
git clone https://github.com/balakrishnanpremnath/sales-analytics-powerbi.git
cd sales-analytics-powerbi
```

### 2. Open the Power BI File

Open:

```text
dashboard/Sales_Analytics_Dashboard.pbix
```

Use Microsoft Power BI Desktop to explore the interactive report.
The screenshots provide a preview without opening Power BI.

### 3. Explore the Pages

- Use page navigation to switch between report sections.
- Apply the available slicers.
- Select chart elements to explore cross-filtered results.
- Clear selections before comparing overall totals.
- Compare product sales rankings with profit rankings.

### 4. Refresh Data When Available

Refreshing requires access to the original source files or a
compatible replacement dataset.

If the report refers to a local path from another computer, update
the relevant source connection in Power Query before refreshing.

Opening a saved report and refreshing its source data are separate
operations.

## Data Documentation Status

The source provider, exact date coverage, row count, and whether
the dataset is real or synthetic are not yet documented here.

These details should be confirmed before using the report to make
claims about a real business or attempting to reproduce the analysis
from the raw data.

## Dataset

The workbook is labelled “Sales Analytics Portfolio Dataset” and
contains sales transactions in a Sri Lankan retail context.
Its notes describe intentional data-quality issues for Power BI
and Power Query practice.

The original creator, download source, and license have not yet
been verified. The data should not be presented as verified
transactions from a named business.

| Dataset Detail | Value |
|---|---|
| Original transaction rows | 3,000 |
| Exact duplicate rows | 10 |
| Rows after removing duplicates | 2,990 |
| Columns | 19 |
| Date coverage | 1 January 2024–31 August 2026 |
| Currency | Sri Lankan Rupees (LKR) |
| Unique customers | 349 |
| Unique products | 25 |

### Data Quality

The supplied workbook contains:

- 10 exact duplicate transaction rows.
- 15 records with missing customer names.
- City values with capitalization or spacing inconsistencies.

Removing the exact duplicate rows produces totals consistent
with the documented dashboard KPIs.

### Metric Definitions

- Sales = Quantity × Unit Price × (1 − Discount)
- Total Cost = Quantity × Unit Cost
- Gross Profit = Sales − Total Cost
- Gross Profit Margin = Gross Profit ÷ Sales

Gross profit does not account for other operating expenses
unless they are included in the recorded unit costs.

## Skills Demonstrated

- Power BI report development
- Power Query data preparation
- DAX measure creation
- KPI definition and interpretation
- Product and customer analysis
- Regional sales analysis
- Interactive filtering and report navigation
- Data visualization and documentation

## Limitations

- KPI values depend on filters and the underlying dataset.
- Rounded dashboard values may differ slightly from calculations
  using the full underlying numbers.
- Profit interpretation depends on the source definition.
- Source documentation and detailed transformation steps remain
  to be added.
- The report provides descriptive analysis; forecasting and
  causal analysis are outside its current scope.

## Planned Improvements

- Document the dataset source, coverage, and row-level structure.
- Summarize the Power Query cleaning steps.
- Add a data-model screenshot.
- Record specific product and regional findings with supporting values.
- Add year-over-year and month-over-month comparisons.
- Add target-versus-actual analysis where suitable target data exists.
- Develop drill-through pages and report tooltips.
  
## Key Findings

Based on the dataset after removing exact duplicate rows:

- Western Province recorded the highest sales at LKR 34.09M.
- Electronics was the largest category by sales at LKR 76.25M.
- The 27-inch Monitor was the highest-selling product by sales
  value at LKR 22.03M.

These findings describe the supplied practice dataset.
They do not establish the causes of sales performance.
## Author

**Balakrishnan Premnath**  
BSc (Hons) in Data Science  
Sri Lanka Technology Campus (SLTC)

[GitHub](https://github.com/balakrishnanpremnath) |
[LinkedIn](https://www.linkedin.com/in/balakrishnan-premnath)
