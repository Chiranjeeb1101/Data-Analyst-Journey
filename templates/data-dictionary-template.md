# Data Dictionary — [Dataset / Table Name]

**Table / Dataset Name**: `[schema_name.table_name]`  
**Grain**: [Define exact representation of one row, e.g., "One row per customer order transaction"]  
**Primary Key**: `[primary_key_column]`  
**Update Frequency**: [e.g., Real-time stream, Daily ETL batch at 02:00 UTC]  
**Data Owner**: [Engineering / Data Platform / Finance Team]

---

## 📋 Schema Definition

| Column Name | Data Type | Nullable? | Foreign Key Reference | Description & Definition | Example Values | Business Logic / Rules |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `order_id` | VARCHAR(36) | NO | None | Unique system identifier for order | `"ord_89231jks"` | Generated upon checkout submission |
| `customer_id` | VARCHAR(36) | NO | `dim_customers.customer_id` | Unique ID of purchasing customer | `"cust_90123"` | Links to customer profile dimension |
| `order_timestamp` | TIMESTAMP | NO | None | Exact UTC timestamp of order placement | `"2026-08-12 14:22:10"` | Converted to UTC during ingestion |
| `gross_amount` | NUMERIC(10,2)| NO | None | Total dollar value before discounts | `149.99` | Must be $\ge 0.00$ |
| `discount_amount` | NUMERIC(10,2)| YES | None | Total discount applied via promo codes | `15.00` | Default to `0.00` if no promo used |
| `net_amount` | NUMERIC(10,2)| NO | None | Final amount billed to customer | `134.99` | Calculated: `gross_amount - discount_amount` |
| `order_status` | VARCHAR(20) | NO | None | Order lifecycle status | `"COMPLETED"`, `"REFUNDED"` | Valid values: `['PENDING', 'COMPLETED', 'CANCELLED', 'REFUNDED']` |

---

## ⚠️ Known Data Quality Issues & Gotchas

1. **Refund Rows**: Refunded orders retain their original `order_id` and have `order_status = 'REFUNDED'`. Always filter `WHERE order_status = 'COMPLETED'` when computing net sales revenue!
2. **Historical Timestamp Format**: Prior to 2025-01-01, timestamps were logged in EST rather than UTC. Use `CONVERT_TIMEZONE('EST', 'UTC', order_timestamp)` for historical trend joins.
