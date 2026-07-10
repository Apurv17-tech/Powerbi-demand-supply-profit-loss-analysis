# Power BI End-to-End Project — Demand, Availability & Profit/Loss Analysis

An end-to-end Power BI project built on a **MySQL → SQL Server → Power BI** pipeline. The project simulates a real production workflow: data starts in MySQL, moves through a SQL Server test environment for prep and validation, transitions to a production SQL Server environment, and is finally modeled and visualized in Power BI Desktop.

## Project Overview

The report tracks product **demand vs. availability** and the resulting **profit/loss impact** of supply shortages, across two report pages.

| Page | Visuals (Card KPIs) |
|---|---|
| **Page 1 — Demand & Availability** | Average Demand Per Day · Average Availability Per Day · Total Supply Shortage |
| **Page 2 — Profit & Loss** | Total Profit · Total Loss · Average Loss Per Day |

**Data model**
- `Demand/Availability Data` — core fact table (product, order date, demand/availability figures)
- `Measures Table` — dedicated table holding the DAX measures used across both report pages

## Workflow / Pipeline

1. **MySQL Server & Workbench** set up as the source system
2. Test data imported into a **SQL Server test environment**
3. **Left Join** applied in SQL Server to shape the data for reporting
4. Data imported into **Power BI Desktop** from the test environment
5. **DAX measures & KPIs** built for both report pages
6. Data imported into a **SQL Server production environment**
7. **Data cleaning in SQL** and transition of the report from test → production
8. **MySQL Connector** installed to connect Power BI directly to MySQL
9. Data imported into a **MySQL database**, with equivalent SQL logic recreated in **MySQL Workbench** to populate a new table
10. Workspace created and report **published** from the SQL Server data source
11. Data re-imported into Power BI from the **MySQL database**
12. Report **transitioned between data sources** using the **Advanced Editor** in Power Query

This mirrors a realistic scenario: prototype against a test database, then cut over to production and even swap the underlying data source (SQL Server → MySQL) without rebuilding the report from scratch.

## Tools Used

- MySQL Server & MySQL Workbench
- Microsoft SQL Server
- Power BI Desktop (Power Query / Advanced Editor, DAX)

## How to Use

1. Open `PROD_PowerBI_Report.pbix` in Power BI Desktop.
2. Point Power Query at your own MySQL or SQL Server instance (see the Advanced Editor step in the pipeline above for how the source was swapped).
3. Refresh the data model to populate the `Demand/Availability Data` table and recalculate the measures.
