# Dimensions vs. Measures & Table Grain

> **Mastering table grain, quantitative measures, categorical dimensions, and aggregation boundaries.**

---

## 🌾 What is Table Grain?

**Table Grain** is the single most critical concept in data analysis and data modeling.

> **Table Grain defines exactly what one single row in a table represents.**

### Examples of Grain

* `orders` table: **One row per completed order.**
* `order_items` table: **One row per item within a specific order.**
* `daily_customer_summary` table: **One row per customer per calendar day.**

> ⚠️ **Critical Rule**: Never join tables without knowing the grain of both tables! Joining an `orders` table to an `order_items` table on `order_id` will duplicate order-level totals unless aggregated first!

---

## 📐 Measures vs. Dimensions

| Attribute | Dimensions (Categorical / Slice) | Measures (Quantitative / Aggregate) |
| :--- | :--- | :--- |
| **Definition** | Qualitative attributes used to filter, group, and slice data | Numerical values that can be aggregated mathematically (SUM, AVG, COUNT) |
| **Examples** | `country`, `product_category`, `device_type`, `signup_cohort` | `revenue`, `quantity_sold`, `discount_amount`, `session_duration_sec` |
| **SQL Placement** | Appears in `GROUP BY`, `WHERE`, `ORDER BY` | Appears inside aggregate functions (`SUM(revenue)`, `AVG(price)`) |
| **BI Placement** | Axis, Legend, Slicers, Rows/Columns in Pivot Tables | Values / Card visuals in Power BI & Excel |
