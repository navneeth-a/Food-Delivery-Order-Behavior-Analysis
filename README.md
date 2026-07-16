# Food-Delivery-Order-Behavior-Analysis - Power BI Project

## Overview

An interactive Power BI dashboard analyzing food ordering patterns across 150 transactions, 15 restaurants, 40 customers, and 10 delivery partners across 4 Indian cities.

## Features

- ✅ Bookmark navigation across 4 pages via buttons
- ✅ Cross-filtering between all visuals on each page
- ✅ Drill-through from Restaurants page to restaurant detail
- ✅ Date hierarchy — Year → Quarter → Month → Day
- ✅ City slicer, Month slicer, and Meal Time slicer
- ✅ Card visuals 
- ✅ Scatter chart — Rating vs Popularity with reference lines
- ✅ Map visual — Revenue by city with bubble sizing

## Key Insights

- 🕖 **Peak order time** — Lunch (41 orders) leads, followed by Breakfast and Snacks
- 🍛 **Top cuisines** — South Indian and American at 16.67% each
- 🏙️ **Top city** — Chennai generates highest revenue at $21.04K
- 💸 **Optimal discount** — 10% discount drives the highest average order value
- 🚴 **Best partners** — Bike-based delivery partners have the lowest avg delivery time
- 📈 **Revenue trend** — Consistent growth from January to June 2025

## Data Model

**5 tables in a Star Schema:**

```
Customers ──┐
Restaurants ─┼──→ Orders (150 rows — Fact table)
DeliveryPartners ─┘     ↑
DateTable ───────────────┘
```

## Concepts

* Data Sourcing
* Data Transform
* Data Modeling
* DAX
* Data Visualization
* Dashboards

## Key DAX Measures

```dax
Total Revenue       = SUM(Orders[FinalAmount])
Cancellation Rate   = DIVIDE([Cancelled Orders], [Total Orders])
Delay Rate          = DIVIDE([Delayed Orders], [Delivered Orders])
Revenue MoM %       = DIVIDE([Total Revenue] - [Previous Month Revenue], [Previous Month Revenue])
Repeat Customer Rate = DIVIDE([Repeat Customers], [Total Customers])
Avg Delivery Delay  = AVERAGEX(FILTER(Orders, Orders[OrderStatus] <> "Cancelled"), Orders[ActualDeliveryMin] - Orders[PromisedDeliveryMin])
```

## Dashboard Pages

| Page             | Focus |
|---               |---
| 🏠 Home         | Revenue overview, city map, cuisine split, peak meal times |
| 📦 Orders       | Peak order hours, order status, payment methods, discount analysis |
| 🍽️ Restaurants  | Top 10 revenue, cuisine performance, rating vs popularity |
| 🚴 Drivers      | Delivery time, delay rate, partner ranking, vehicle split |

## Tools Used

* Power BI Desktop
* Power Query
* Data Modeling

## Files Included

* Dataset
* Data Visual Proj.pbix (Power BI File)
* Dashboards (Images)
* README.md

## How to Run

1. Download [Power BI Desktop](https://powerbi.microsoft.com/desktop)
2. Clone this repository
3. Open `Data Visual Proj.pbix` file
5. Click **Refresh**
