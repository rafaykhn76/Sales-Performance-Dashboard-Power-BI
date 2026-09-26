# Sales Performance Dashboard — Power BI Project

## 📊 Project Overview

This project is an end-to-end Power BI dashboard built to analyze sales performance against targets across regions, product categories, and individual salespeople. It uses a multi-table sales dataset (Sales, Targets, Product, Region, Salesperson, Reseller) connected through a proper star-schema data model.

The dashboard tracks total sales, target achievement, units sold, and profit, and includes an interactive scatter chart comparing individual sales volume against target achievement percentage.

## 🖼️ Dashboard Preview

![Sales Performance Dashboard](Power%20bi%20Dashboard%20.png)

## 🔧 Data Modeling

- Built a star-schema model connecting 8 tables: Sales Sheet, Targets, Product, Region, Salesperson, SalespersonRegion, Reseller, and a custom Calendar table.
- Created a Calendar table using `CALENDARAUTO()` and marked it as the official date table.
- Fixed a data quality issue where the `TargetMonth` column was stored as a whole number instead of a date, which prevented it from relating to the Calendar table. Corrected the data type and rebuilt the relationship.

## 📐 DAX Measures

Key measures written for this project:

```dax
Total Sales = SUM('Sales Sheet'[Sales])
Total Target = SUM(Targets[Target])
Target Achievement % = DIVIDE([Total Sales], [Total Target])
Units Sold = SUM('Sales Sheet'[Quantity])
Total Cost = SUM('Sales Sheet'[Cost])
Profit = [Total Sales] - [Total Cost]
Profit Margin % = DIVIDE([Profit], [Total Sales])
```

## 📈 Visualizations

The dashboard includes six visual types:

- KPI cards: Total Sales, Total Target, Target Achievement %, Units Sold
- Line chart: Total Sales vs Total Target by Month
- Donut chart: Total Sales by Region
- Bar chart: Total Sales by Category
- Table: Salesperson performance (Total Sales, Total Target, Target Achievement %)
- Scatter chart: Total Sales vs Target
