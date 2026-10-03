# excel-power-pivot-sales-dashboard
An interactive Excel sales dashboard built with Power Pivot, star schema data modeling, and custom DAX measures for executive revenue analysis.

# Executive Sales Dashboard (Power Pivot & DAX)

An end-to-end Excel data modeling and dashboard project built using **Power Pivot** and **DAX (Data Analysis Expressions)**. 

This project transforms transactional sales data into an interactive executive reporting tool, eliminating the need for traditional `VLOOKUP`/`XLOOKUP` formulas by structuring the data into a relational star schema.

---

## Project Overview

The objective of this project is to analyze customer buying behavior, regional sales performance, and product line trends. By leveraging Excel's Data Model and explicit DAX measures, the dashboard updates dynamically when underlying data changes or when filtered via interactive slicers.

### Key Deliverables:
* **Relational Star Schema:** Linked three core tables (`Customers`, `Products`, and `Sales`) using 1-to-Many relationships.
* **Custom DAX Measures:** Developed explicit measures for tracking volume, distinct order counts, average quantities, and total revenue across related tables.
* **Interactive Executive Dashboard:** Built clean visual KPIs, summary cards, and PivotCharts filtered by a dynamic regional slicer.

---

## Data Architecture & Schema

The data model is built on a **Star Schema** centered around transactional sales records:

* **Fact Table:** `Sales` *(Order ID, Order Date, Customer ID, Product ID, Quantity)*
* **Dimension Table:** `Customers` *(Customer ID, Customer Name, Region)*
* **Dimension Table:** `Products` *(Product ID, Product Name, Category, Unit Price)*

### Data Model Relationships:
1. `Customers[Customer ID]` ─── (1 : N) ───> `Sales[Customer ID]`
2. `Products[Product ID]` ─── (1 : N) ───> `Sales[Product ID]`

---

## DAX Measures Implemented

All metrics were authored inside Power Pivot using explicit DAX calculations:

| Measure Name | DAX Formula | Description |
| :--- | :--- | :--- |
| **Total Quantity** | `SUM(Sales[Quantity])` | Aggregates overall units sold. |
| **Average Quantity** | `AVERAGE(Sales[Quantity])` | Calculates mean units per transaction line item. |
| **Order Count** | `COUNT(Sales[Order ID])` | Counts total sales line items across the dataset. |
| **Distinct Order Count** | `DISTINCTCOUNT(Sales[Order ID])` | Tracks unique order transactions. |
| **Total Sales** | `SUMX(Sales, Sales[Quantity] * RELATED(Products[Unit Price]))` | Iterates row-by-row across `Sales` to evaluate revenue using prices from `Products`. |

---

## Dashboard Features

* **Executive Summary Header:** Clean summary text highlighting overall performance metrics.
* **Regional Breakdown:** Visual representation of sales performance across North, South, East, and West regions.
* **Product Line Breakdown:** Performance tracking across categories (Apparel, Accessories, Jewelry, Beauty).
* **Dynamic Slicer Integration:** Single-click region filtering that updates all KPIs and charts simultaneously.

---

## Tools & Technologies Used

* **Microsoft Excel** (Excel 365 / Power Pivot enabled)
* **DAX (Data Analysis Expressions)**
* **Power Pivot Data Model**
* **PivotTables & PivotCharts**
