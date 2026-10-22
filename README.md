# Financs-BI-Intellengence-
# 📊 Finance & BI Performance Dashboard

## 📌 1. Project Overview
- <img width="801" height="456" alt="Screenshot 2026-10-08 124543" src="https://github.com/user-attachments/assets/09bb0c6d-46c1-4364-9fdd-d467d8117fcf" />


The Finance & BI Performance Dashboard is an interactive business intelligence project developed using Microsoft Power BI to analyze financial and sales performance.

The dashboard provides a consolidated view of key performance indicators (KPIs), yearly profit trends, product sub-category sales, shipping performance, regional profitability, customer contributions, product rankings, and geographic sales distribution.

The purpose of this project is to transform raw business data into meaningful insights that help stakeholders monitor performance, identify trends, evaluate business segments, and make informed decisions.

## 🎯 2. Project Objectives

- Monitor overall sales and profitability.
- Track yearly profit performance and changes over time.
- Analyze sales across product sub-categories.
- Compare profit contributions by shipping mode.
- Evaluate regional profitability.
- Identify top-performing customers and products.
- Explore sales distribution across countries.
- Provide interactive filters for exploring business performance.
- Support data-driven decision-making through visual analytics.

## 🧰 3. Tools and Technologies

- **Microsoft Power BI Desktop:** Dashboard development and interactive reporting.
- **DAX (Data Analysis Expressions):** KPI calculations and analytical measures.
- **Power Query:** Data cleaning and transformation, where used.
- **Power BI Visualizations:** KPI cards, line charts, bar charts, donut charts, and maps.
- **GitHub:** Project documentation and portfolio presentation.

## 📈 4. Dashboard KPIs

### Total Profit
Measures the overall profit generated within the selected reporting period and filter context.

### Total Sales
Measures the total sales value recorded in the dataset.

### Average Orders
Displays an order-related performance metric. The exact formula should be confirmed to determine whether it represents average order value, average order count, or another measure.

### Average Quantity
Displays a quantity-related metric. Confirm whether this represents average quantity per order or total quantity, and ensure the KPI label accurately describes the calculation.

### KPI Performance Indicators
The dashboard includes percentage comparisons, such as changes versus the previous year or month. These comparisons help users evaluate whether performance has improved or declined over the selected period.

*Note: The screenshot displays approximately 1.47M Total Profit, 13M Total Sales, 505.01 Average Orders, and 178K Average Quantity. Validate these figures and KPI definitions against the actual Power BI report before publishing them as confirmed results.*

## 📊 5. Dashboard Visualizations

### 5.1 Yearly Profit Trend

A line chart displays profit performance from 2019 to 2024.

**Purpose:**
- Monitor changes in profit over time.
- Identify periods of growth or decline.
- Compare performance across reporting years.
- Identify years that may require further investigation.

### 5.2 Total Sales by Sub-Categories

A column chart compares sales across product sub-categories.

**Purpose:**
- Identify high-performing product categories.
- Compare sales contributions across sub-categories.
- Identify categories with relatively low sales.
- Support product planning and marketing analysis.

### 5.3 Total Profit by Ship Mode

A donut chart compares profit contributions across shipping modes, including Standard Class, Second Class, First Class, and Same Day.

**Purpose:**
- Compare profit distribution by shipping method.
- Understand how profit is distributed across delivery options.
- Identify shipping segments for further cost and profitability analysis.

### 5.4 Total Profit by Region

A bar chart compares profit across business regions.

**Purpose:**
- Identify regions contributing the most profit.
- Compare regional financial performance.
- Investigate differences in profitability.
- Support regional business planning.

### 5.5 Top 5 Customers

A ranked bar chart displays the five highest-performing customers according to the measure used in the report.

**Purpose:**
- Identify major contributors to business performance.
- Understand customer concentration.
- Support customer relationship management.
- Identify opportunities for customer retention.

*Confirm whether the ranking is based on sales or profit and label the visual accordingly.*

### 5.6 Top 10 Products

A ranked bar chart displays the ten leading products according to the selected performance metric.

**Purpose:**
- Identify products with strong sales or profit contributions.
- Compare product performance.
- Support inventory and product planning.
- Identify products requiring further performance analysis.

### 5.7 Sales by Country

A geographic map displays the distribution of sales across countries.

**Purpose:**
- Compare sales distribution geographically.
- Identify markets with higher sales contributions.
- Explore potential regional growth opportunities.
- Support geographic performance analysis.

### 5.8 Interactive Filters

The dashboard includes filters for:

- **Year:** Explore performance across different reporting years.
- **Ship Mode:** Focus on specific shipping methods.
- **Category:** Analyze performance for selected product categories.

These filters allow users to explore the dashboard dynamically and compare results across different business segments.

## 🧮 6. Data Analysis and DAX Measures

The following DAX formulas are examples for documenting and implementing the dashboard. Replace the table and column names with the exact names in your Power BI data model.

Assume the sales table is named `Sales`.

### 6.1 Total Sales

```dax
Total Sales =
SUM ( Sales[Sales] )
```

Calculates total sales in the current filter context.

### 6.2 Total Profit

```dax
Total Profit =
SUM ( Sales[Profit] )
```

Calculates total profit in the current filter context.

### 6.3 Profit Margin (%)

```dax
Profit Margin (%) =
DIVIDE (
    [Total Profit],
    [Total Sales],
    0
)
```

Calculates profit as a proportion of sales. Format the measure as a percentage.

### 6.4 Total Quantity

```dax
Total Quantity =
SUM ( Sales[Quantity] )
```

Calculates the total quantity recorded in the dataset.

### 6.5 Total Orders

If each order has a unique order identifier:

```dax
Total Orders =
DISTINCTCOUNT ( Sales[Order ID] )
```

This counts unique orders rather than individual transaction rows.

### 6.6 Average Order Value

```dax
Average Order Value =
DIVIDE (
    [Total Sales],
    [Total Orders],
    0
)
```

Calculates average sales value per distinct order.

### 6.7 Average Quantity per Order

```dax
Average Quantity per Order =
DIVIDE (
    [Total Quantity],
    [Total Orders],
    0
)
```

Calculates the average quantity associated with each order.

### 6.8 Profit by Region

```dax
Profit by Region =
[Total Profit]
```

Use the Region field on the chart axis and this measure as the value. Power BI calculates the regional result through filter context.

### 6.9 Profit by Ship Mode

```dax
Profit by Ship Mode =
[Total Profit]
```

Use the Ship Mode field as the legend and this measure as the value.

### 6.10 Sales by Sub-Category

```dax
Sales by Sub-Category =
[Total Sales]
```

Use the Sub-Category field on the chart axis to compare sales across product sub-categories.

### 6.11 Sales by Country

```dax
Sales by Country =
[Total Sales]
```

Use the Country field in the map location field and this measure to represent sales.

### 6.12 Previous Year Profit

For time intelligence, create a continuous Calendar table with a Date column and a relationship to the sales table.

```dax
Previous Year Profit =
CALCULATE (
    [Total Profit],
    DATEADD (
        'Calendar'[Date],
        -1,
        YEAR
    )
)
```

### 6.13 Profit Change (%)

```dax
Profit Change (%) =
DIVIDE (
    [Total Profit] - [Previous Year Profit],
    [Previous Year Profit],
    0
)
```

This calculates the percentage change in profit relative to the previous year. Format the measure as a percentage.

### 6.14 Sales Change (%)

```dax
Previous Year Sales =
CALCULATE (
    [Total Sales],
    DATEADD (
        'Calendar'[Date],
        -1,
        YEAR
    )
)
```

```dax
Sales Change (%) =
DIVIDE (
    [Total Sales] - [Previous Year Sales],
    [Previous Year Sales],
    0
)
```

These measures can support KPI comparison indicators when the reporting period and filter context are set correctly.
 - ## clean dataset
 - <img width="1335" height="555" alt="Screenshot 2026-10-22 125244" src="https://github.com/user-attachments/assets/eeb87ed1-3b29-4587-ab50-73a2c738f3b7" />


## 🔎 7. Key Analysis Questions

This dashboard can help investigate the following questions:

1. How has profit changed from 2019 to 2024?
2. Which product sub-categories contribute the most sales?
3. Which shipping mode contributes the most profit?
4. Which regions generate the highest profit?
5. Which customers contribute the most to the selected performance metric?
6. Which products rank highest by sales or profit?
7. How are sales distributed across countries?
8. Does profit increase alongside sales?
9. How do results change when filtering by year, category, or ship mode?
10. Which areas require further investigation to improve business performance?

## 💡 8. Business Recommendations

The following recommendations should be validated against the underlying data before being presented as final findings.

### Improve Profitability
Monitor profit and profit margin alongside sales. Investigate situations where sales increase but profit margins decline.

### Optimize Product Performance
Review high- and low-performing sub-categories using sales, profit, discounting, and cost information before making inventory or promotional decisions.

### Evaluate Shipping Performance
Compare profitability across shipping modes and investigate the contribution of shipping costs, delivery performance, and customer requirements.

### Strengthen Regional Performance
Investigate differences in regional profit using sales volume, product mix, costs, and discounts to identify practical improvement opportunities.

### Improve Customer Retention
Study purchasing patterns among high-value customers and evaluate suitable retention and customer engagement initiatives.

### Review Product Portfolio
Use both sales and profit measures to evaluate products. High sales alone do not necessarily indicate high profitability.

### Explore Geographic Opportunities
Validate country-level results and consider market size, operating costs, and other relevant factors before making expansion decisions.

### Establish Regular KPI Monitoring
Review key metrics consistently and document their definitions, reporting periods, and comparison methods to support reliable business decisions.

## ⚠️ 9. Project Limitations

- **Data Quality:** Missing, duplicated, or inaccurate records may affect the reliability of results.
- **KPI Definitions:** Average Orders and Average Quantity must be checked against the actual calculations to ensure that their labels are accurate.
- **Historical Data:** The dashboard describes available historical performance and does not automatically forecast future results.
- **Filter Context:** KPI values can change when users select different years, categories, or shipping modes.
- **Geographic Accuracy:** Map results depend on complete and correctly identified country information.
- **Causality:** Trends and comparisons do not independently establish the causes of business outcomes.
- **Screenshot Values:** The displayed values may be rounded and should be checked against the final report.
- **Example DAX:** The formulas in this documentation must be adapted to the actual table names, column names, and data structure.

## 📚 10. Data Sources and References

Add the actual dataset source and attribution before publishing the project.

- **Dataset Source:** `[Insert the actual dataset name and URL]`
- **Microsoft Power BI Documentation:** https://learn.microsoft.com/en-us/power-bi/
- **DAX Function Reference:** https://learn.microsoft.com/en-us/dax/
- **Power Query Documentation:** https://learn.microsoft.com/en-us/power-query/


Only include data files if you have permission to share them. If the dataset is confidential or too large, provide the original source or instructions for accessing it instead.

## 👤 13. Author

**Peter Kess**

- **Portfolio:** https://canva.link/a3iaibbhnnz0b75
- **LinkedIn:** https://www.linkedin.com/in/kess-peter-bb851

## ✅ 14. Conclusion

The Finance & BI Performance Dashboard demonstrates how Power BI can combine sales, profitability, customer, product, shipping, regional, and geographic information into an interactive business intelligence report.

By bringing key performance indicators and supporting visualizations together, the dashboard helps users monitor business performance, investigate trends, and identify opportunities for further analysis and improvement.
