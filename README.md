# ✈️ Aerospace Supply Chain Performance & Forecasting (SQL Portfolio Project)

An end-to-end SQL analytics project analyzing 3 years of aerospace supply chain data — purchase orders, inventory history, supplier quality, and parts master — to answer the questions a CEO and supply chain leadership team would actually ask.

## 📌 Business Problem

The company sources flight-critical and non-critical parts from 40 suppliers across 6 sites. Leadership needs visibility into three things: **delivery reliability, inventory risk, and supplier quality/spend concentration** — to decide where to intervene first.

## 🎯 Objectives

- Design a clean relational schema for supply chain fact/dimension data
- Validate and clean raw source data before analysis
- Build core supply chain KPIs: OTIF, lead-time variance, stockout exposure, forecast accuracy, supplier risk
- Surface actionable, CEO-ready business insights
- Demonstrate the full range of SQL skills used in a real analyst role: joins, subqueries, CTEs, window functions, ranking functions, views, and stored procedures

## 🗂️ Dataset

| File | Rows | Description |
|---|---|---|
| `parts_master.csv` | 300 | Part catalog: family, criticality, cost, lead time, supplier, risk class |
| `purchase_orders.csv` | 29,666 | PO-level order, promised, and receipt dates + quantities |
| `quality_incidents.csv` | 368 | Defect/non-conformance events by part, supplier, severity |
| `supply_chain_history.csv` | 280,800 | Weekly inventory, consumption, backorder, and forecast snapshots |

## 🏗️ Project Structure

```
sql/
  01_schema.sql               -- table + index creation (T-SQL / SSMS)
  02_data_import.sql          -- BULK INSERT load scripts + import troubleshooting notes
  03_data_cleaning.sql        -- data quality validation & standardization
  04_exploratory_analysis.sql -- EDA: joins, GROUP BY, CASE, date functions
  05_kpi_analysis.sql         -- core KPIs: CTEs, window functions, ranking functions
  06_advanced_analysis.sql    -- LAG/LEAD, running totals, multi-CTE risk matrix
  07_views.sql                -- reusable reporting views
  08_stored_procedures.sql    -- parameterized supplier/stockout/forecast procs
data/
  *.csv                       -- source dataset
EXECUTIVE_SUMMARY.md          -- CEO-facing findings & recommendations
```

## 🧠 SQL Concepts Demonstrated

| Category | Where |
|---|---|
| Joins (inner, left) | `04`, `05`, `06`, `07` |
| Subqueries (scalar, correlated, IN) | `05` |
| CTEs (single & multi-level) | `05`, `06`, `07` |
| Window functions (`SUM() OVER`, `AVG() OVER`, moving average) | `05`, `06` |
| Ranking functions (`RANK`, `DENSE_RANK`, `ROW_NUMBER`, `NTILE`) | `05`, `06` |
| `LAG` / `LEAD` | `06` |
| Aggregate functions | `04`, `05` |
| `CASE` expressions | `03`, `04`, `05` |
| Date functions (`DATEDIFF`, `DATEPART`, `DATEFROMPARTS`) | `04`, `05`, `06` |
| Views | `07` |
| Stored procedures with parameters & error handling | `08` |

## 📊 Key KPIs Built

- **OTIF (On-Time-In-Full) rate** — overall and by supplier
- **Lead-time variance** — promised vs. actual receipt date
- **Stockout exposure** — % of weeks with backorders, by part criticality
- **Forecast accuracy** — rolling 4-week average forecast error
- **Supplier risk matrix** — suppliers who are simultaneously high-spend and high-defect

## 🔑 Headline Findings

- Company-wide OTIF is only **39.7%** — a systemic delivery reliability problem
- **6 suppliers** are both top-quartile spend and top-quartile defect risk, representing ~$153M of $593M total 3-year spend
- Flight-critical (Class A) parts have the lowest stockout rate (0.28%) but still saw 124 stockout-weeks
- Average forecast error is ~65% relative to average weekly consumption — a real demand-planning opportunity

Full findings and recommendations: see [`EXECUTIVE_SUMMARY.md`](./EXECUTIVE_SUMMARY.md)

## 🛠️ Tools

- **SQL Server (T-SQL)** via SQL Server Management Studio (SSMS)
- Dataset sourced as CSV, loaded via `BULK INSERT`

## 🚀 How to Run

1. Run `sql/01_schema.sql` to create the database and tables
2. Update the file paths in `sql/02_data_import.sql` to point to your local `/data` folder, then run it
3. Run `sql/03_data_cleaning.sql` to validate the load
4. Run `04` → `08` in order to reproduce the full analysis, views, and procedures

## 👤 Author

**Sandipan Roy**
[GitHub](https://github.com/sandipanroy33) · [LinkedIn](https://linkedin.com/in/SandipanRoy19)
