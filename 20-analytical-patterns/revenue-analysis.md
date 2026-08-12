# Analytical Playbook — Revenue Analysis & Decomposition

> **Standard operating playbook for diagnosing revenue trends, driver isolation, and top-line performance.**

---

## 🎯 When to Use This Playbook
Use this playbook when revenue increases or decreases unexpectedly, when performing quarterly business reviews (QBRs), or when evaluating product/segment performance.

---

## ❓ Core Business Questions
1. Is revenue change driven by customer volume (orders/users) or pricing/basket size (AOV)?
2. Which customer segment (New vs Returning, Geographic Region, Tier) accounts for the largest variance?
3. What is the impact of discounts, refunds, and promo codes on net revenue?

---

## 📐 Mathematical Decomposition Formula

$$\text{Net Revenue} = (\text{Order Volume} \times \text{Average Order Value}) - \text{Refunds} - \text{Discounts}$$

$$\text{Order Volume} = \text{Active Purchasing Customers} \times \text{Purchase Frequency}$$

---

## 💻 SQL Query Pattern (PostgreSQL / Snowflake / BigQuery)

```sql
WITH monthly_revenue_breakdown AS (
    SELECT
        DATE_TRUNC('month', order_date) AS revenue_month,
        COUNT(DISTINCT customer_id) AS active_buyers,
        COUNT(order_id) AS total_orders,
        SUM(gross_amount) AS gross_revenue,
        SUM(discount_amount) AS total_discounts,
        SUM(net_amount) AS net_revenue,
        -- Calculate Key Metrics
        SUM(net_amount) / NULLIF(COUNT(order_id), 0) AS average_order_value,
        COUNT(order_id)::NUMERIC / NULLIF(COUNT(DISTINCT customer_id), 0) AS purchase_frequency
    FROM orders
    WHERE order_status = 'COMPLETED'
    GROUP BY 1
)
SELECT
    revenue_month,
    active_buyers,
    total_orders,
    gross_revenue,
    net_revenue,
    average_order_value,
    purchase_frequency,
    -- Month-over-Month Net Revenue Growth
    LAG(net_revenue) OVER (ORDER BY revenue_month) AS prior_month_revenue,
    ROUND(
        (net_revenue - LAG(net_revenue) OVER (ORDER BY revenue_month)) / 
        NULLIF(LAG(net_revenue) OVER (ORDER BY revenue_month), 0) * 100, 2
    ) AS mom_net_revenue_growth_pct
FROM monthly_revenue_breakdown
ORDER BY revenue_month DESC;
```

---

## 🐍 Python / Pandas Implementation

```python
import pandas as pd

def analyze_revenue(df: pd.DataFrame) -> pd.DataFrame:
    """
    Decomposes net revenue into Active Buyers, Order Volume, AOV, and MoM Growth.
    Expects DataFrame with columns: ['order_date', 'customer_id', 'order_id', 'net_amount']
    """
    df['order_date'] = pd.to_datetime(df['order_date'])
    df['revenue_month'] = df['order_date'].dt.to_period('M')
    
    monthly = df.groupby('revenue_month').agg(
        active_buyers=('customer_id', 'nunique'),
        total_orders=('order_id', 'count'),
        net_revenue=('net_amount', 'sum')
    ).reset_index()
    
    monthly['aov'] = monthly['net_revenue'] / monthly['total_orders']
    monthly['purchase_frequency'] = monthly['total_orders'] / monthly['active_buyers']
    monthly['mom_growth_pct'] = monthly['net_revenue'].pct_change() * 100
    
    return monthly
```

---

## 📊 Recommended Visualization
* **Waterfalls Chart**: To show bridge from Gross Revenue → Discounts → Refunds → Net Revenue.
* **Dual-Axis / Combo Chart**: Line for MoM Net Revenue Growth % and Bars for Order Volume vs AOV.

---

## 💡 Executive Recommendation Framework
* If **Active Buyers ↓** but **AOV ↑**: Revenue is being sustained by a shrinking pool of high-spend customers; acquisition or top-funnel marketing needs urgent attention.
* If **Discounts ↑** but **Net Revenue Flat**: Discounting is diluting margin without driving incremental volume; recommend cutting promo thresholds.
