# Supplier Price Analysis Dashboard

A procurement analytics dashboard built using Microsoft Power BI to track supplier-wise product price changes over time and detect unusual pricing situations.

---

## Project Overview

This project analyzes historical and current supplier pricing data for products purchased by a company. The dashboard helps identify:

- Supplier-wise price increases/decreases
- Unusual pricing patterns
- Vendor pricing inconsistencies
- Procurement risk indicators

The dashboard was created as a business intelligence solution for procurement and supplier monitoring.

---

## Problem Statement

The objective was to help company executives monitor supplier pricing trends from past to present and identify abnormal price changes for products purchased from suppliers.

---

## Features

- Historical vs Latest Price Comparison
- Supplier-wise Price Trend Analysis
- Price Increase % Calculation
- Price Decrease % Detection
- Unusual Price Increase Identification
- Major Price Drop Detection
- Conditional Formatting for Anomaly Detection
- Interactive Power BI Visualizations

---

## Tools & Technologies Used

- Microsoft Power BI
- Power Query
- DAX
- Data Transformation
- Data Modeling

---

## Dataset Columns

The dataset includes:

- Product Name
- Supplier
- Unit Price
- Date Entered
- Category
- Units In Stock
- Units On Order
- Reorder Level
- Discontinued Status

---

## Data Processing Steps

### 1. Data Cleaning
- Imported raw supplier data into Power BI
- Sorted data by Product, Supplier, and Date

### 2. Earliest & Latest Price Tracking
- Used Group By aggregations
- Extracted:
  - Earliest Purchase Date
  - Latest Purchase Date

### 3. Merge Operations
Merged grouped datasets with original tables to retrieve:
- Earliest Price
- Latest Price

### 4. Custom Calculations

#### Price Increase %

DAX

DIVIDE(
    [Latest Price] - [Earliest Price],
    [Earliest Price]
)

###Price Status Classification

DAX

IF(
    [Price Increase %] > 0.30,
    "Unusual Increase",
    IF(
        [Price Increase %] < -0.20,
        "Major Decrease",
        "Normal"
    )
)
