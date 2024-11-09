# Power BI Sales Dashboard | Power BI End-to-End Project

This repository provides a step-by-step approach to creating a comprehensive sales analysis dashboard that visualizes key performance indicators (KPIs), sales trends, and comparative analysis using Power BI.
[Dashboard](https://github.com/jaykells/PowerBI-Sales-Dashboard/raw/aad95203a447ead6ba69a701b636da89ff7a36fb/Sales%20Dashboard.pbix)

## Project Objectives

This project demonstrates how to:
- Calculate and visualize total sales, profit, orders, and profit margin.
- Compare year-over-year sales and profit performance by product, month, and sales channel.
- Analyze sales by customer and highlight top-performing locations.
- Create dynamic, interactive dashboards with slicers for user-friendly filtering by Date, City, Product, and Channel.

### Key Features
1. **Total Sales Calculation**: A complete sales overview for the selected period.
2. **Profit and Profit Margin Analysis**: Financial performance visualizations.
3. **Year-Over-Year Comparisons**: Insights into product performance and monthly trends.
4. **Top 5 Cities Analysis**: Highlights most lucrative locations for focused marketing.
5. **Customer Sales Analysis**: Detailed customer-level insights.
6. **Dynamic Slicers**: Filters for personalized data interaction.

## Folder Structure
- **Dashboard_Screenshots/**: Contains screenshots of each major dashboard visualization.
- **PBIX_File/**: Contains the Power BI project file for easy access and edits.
- **Documentation/**: Additional documentation on project objectives, data preparation, data modeling, visualization design, and DAX implementation.

## Skills Demonstrated
- **Power BI Reporting & Visualization**
- **Data Cleaning & Preparation**
- **Data Modeling & Relationship Building**
- **DAX Calculations**
- **Sales & Profit Analysis**

## Future Work
This dashboard provides foundational insights into sales performance. Future iterations could explore:
- Enhanced customer segmentation analysis.
- Predictive sales modeling for better forecasting.
- Expanded dashboards for additional business areas.

# PowerBI-Sales-Dashboard

## Steps Followed to Create Power BI Sales Dashboard
1. **Gather Data**: Sample data used for dashboard creation. [Excel.](https://github.com/jaykells/PowerBI-Sales-Dashboard/raw/refs/heads/main/Sales%20Analysis%20Report.xlsx)
2. **Power Query – Data Extract, Transform & Load**: Power Query Editor in Power BI was used for data cleaning and transformation making it suitable for analysis. This involved removing duplicates, handling missing values, merging datasets, and creating calculated columns.
3. **Create a Date Table**: To work with Data Analysis Expressions (DAX) time intelligence functions, there’s a prerequisite model requirement - To have at least one [date table](https://learn.microsoft.com/en-us/power-bi/guidance/model-date-tables).
**Creating a Simple Date Table in Power BI using DAX**

 - Open Power BI Desktop and click on the “Modeling” tab.
 - Click on “New Table” to create a new table.
 - In the formula bar, enter the following DAX formula to create a date table:

```dax
DAX DateTable = 
ADDCOLUMNS (
    //CALENDAR(DATE(2020,1,1), DATE(2024,12,31)),
    CALENDARAUTO(),
    "Year", YEAR([Date]),
    "Quarter", "Q" & FORMAT(CEILING(MONTH([Date])/3, 1), "#"),
    "Quarter No", CEILING(MONTH([Date])/3, 1),
    "Month No", MONTH([Date]),
    "Month Name", FORMAT([Date], "MMMM"),
    "Month Short Name", FORMAT([Date], "MMM"),
    "Month Short Name Plus Year", FORMAT([Date], "MMM,yy"),
    "DateSort", FORMAT([Date], "yyyyMMdd"),
    "Day Name", FORMAT([Date], "dddd"),
    "Details", FORMAT([Date], "dd-MMM-yyyy"),
    "Day Number", DAY ( [Date] )
)
4. **Create Data Model**: Designed a data model to represent relationships between tables, define keys, and establish hierarchies for accurate analysis and visualization.

5. **Develop Reports**: Built interactive reports with visualizations (charts, tables, maps) in Power BI Desktop. Implemented slicers for Date, City, Product, and Channel, with drill-through capabilities.

- Sales by Product (compared to last year)
- Sales by Month (compared to last year)
- Top 5 Cities by Sales
- Profit by Channel (compared to last year)
- Sales by Customer (compared to last year)
Key Metrics: Sales, Profit, Profit Margin, Products Sold
6. **Implement DAX Calculations**: Used DAX to create measures and calculated columns for advanced calculations:

Sales: Sales = SUM(Sales_Data[Sales])
Sales PY: Sales PY = CALCULATE([Sales], SAMEPERIODLASTYEAR(DateTable[Date]))
Sales vs PY: Sales vs PY = [Sales] - [Sales PY]
YOY% Change: Sales vs py % = DIVIDE([Sales vs PY],[Sales],0)
Profit: Profit = SUM(Sales_Data[Profit])
Profit vs LY: Profit Vs LY = [Profit] - CALCULATE([Profit], SAMEPERIODLASTYEAR(DateTable[Date]))
Profit Margin: Profit Margin = DIVIDE([Profit],[Sales],0)
**Conclusion**:

Sales decreased by more than 10% in 2019.
Top 7 products saw a decline in sales.
Four customers contributed to the drop in sales.
Profit margin was higher in the Export channel.
