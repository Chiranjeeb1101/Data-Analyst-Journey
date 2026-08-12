# Analytical Playbook — Customer Segmentation & RFM Analysis

> **Standard operating playbook for segmenting customers based on Recency, Frequency, and Monetary (RFM) behavioral metrics.**

---

## 🎯 When to Use This Playbook
Use this playbook to group customers into actionable tiers (e.g., Champions, At-Risk, Lost, High-Value) for targeted marketing, retention campaigns, and VIP loyalty programs.

---

## ❓ Core Business Questions
1. Who are our top 10% most valuable customers ("Champions")?
2. Which previously active, high-spending customers are showing signs of slipping away ("At-Risk")?
3. How should marketing budget and promotional discounts be allocated across customer segments?

---

## 📐 RFM Definitions

* **Recency (R)**: Days elapsed since the customer's last purchase. (Lower is better!)
* **Frequency (F)**: Total number of orders placed by the customer. (Higher is better!)
* **Monetary Value (M)**: Total dollar amount spent by the customer. (Higher is better!)

---

## 💻 SQL Query Pattern (PostgreSQL / Snowflake / BigQuery)

```sql
WITH customer_rfm_raw AS (
    SELECT
        customer_id,
        CURRENT_DATE - MAX(order_date)::DATE AS recency_days,
        COUNT(order_id) AS frequency_count,
        SUM(net_amount) AS monetary_val
    FROM orders
    WHERE order_status = 'COMPLETED'
    GROUP BY customer_id
),
rfm_scores AS (
    SELECT
        customer_id,
        recency_days,
        frequency_count,
        monetary_val,
        -- Assign scores 1 to 4 using NTILE window functions
        NTILE(4) OVER (ORDER BY recency_days DESC) AS r_score, -- Reversed so high recent activity = score 4
        NTILE(4) OVER (ORDER BY frequency_count ASC) AS f_score,
        NTILE(4) OVER (ORDER BY monetary_val ASC) AS m_score
    FROM customer_rfm_raw
),
rfm_segments AS (
    SELECT
        *,
        (r_score * 100 + f_score * 10 + m_score) AS rfm_combined,
        CASE
            WHEN r_score = 4 AND f_score = 4 AND m_score = 4 THEN 'Champions'
            WHEN r_score >= 3 AND f_score >= 3 THEN 'Loyal Customers'
            WHEN r_score <= 2 AND f_score >= 3 THEN 'At Risk - Winback'
            WHEN r_score <= 1 AND f_score <= 1 THEN 'Lost Customers'
            ELSE 'Promising / Recent Buyers'
        END AS customer_segment
    FROM rfm_scores
)
SELECT
    customer_segment,
    COUNT(customer_id) AS total_customers,
    ROUND(AVG(recency_days), 1) AS avg_recency_days,
    ROUND(AVG(frequency_count), 1) AS avg_frequency_orders,
    ROUND(AVG(monetary_val), 2) AS avg_monetary_spend,
    ROUND(SUM(monetary_val), 2) AS segment_total_revenue
FROM rfm_segments
GROUP BY customer_segment
ORDER BY segment_total_revenue DESC;
```

---

## 💡 Executive Action Matrix

| Segment | Strategy | Actionable Recommendation |
| :--- | :--- | :--- |
| **Champions** | Reward & Retain | Provide VIP early access to new product releases; no heavy discounting needed. |
| **At Risk - Winback** | Reactivate | Deploy targeted win-back email sequences with personalized incentive discounts. |
| **Lost Customers** | Evaluate Spend | Limit expensive direct ad spend; use low-cost automated email check-ins. |
