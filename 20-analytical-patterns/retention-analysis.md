# Analytical Playbook — Customer Retention Analysis

> **Standard operating playbook for evaluating user retention curves, churn thresholds, and repeat activity.**

---

## 🎯 When to Use This Playbook
Use this playbook to assess product-market fit, track long-term customer health, evaluate onboarding effectiveness, and calculate customer payback periods.

---

## ❓ Core Business Questions
1. What percentage of newly acquired users return to perform a key event (purchase/login) N days/weeks/months after signup?
2. At what point does the retention curve flatten (indicating sustainable long-term retention)?
3. Which customer acquisition channels yield the highest 90-day retention rates?

---

## 💻 SQL Query Pattern (Cohort N-Month Retention)

```sql
WITH customer_first_order AS (
    -- Identify cohort month for each customer
    SELECT
        customer_id,
        DATE_TRUNC('month', MIN(order_date)) AS cohort_month
    FROM orders
    GROUP BY customer_id
),
customer_activity AS (
    -- Map subsequent orders to cohort month and calculate month offset
    SELECT
        c.cohort_month,
        DATE_TRUNC('month', o.order_date) AS activity_month,
        -- Calculate month index (0 = signup month, 1 = Month +1, etc.)
        (EXTRACT(YEAR FROM o.order_date) - EXTRACT(YEAR FROM c.cohort_month)) * 12 +
        (EXTRACT(MONTH FROM o.order_date) - EXTRACT(MONTH FROM c.cohort_month)) AS month_number,
        o.customer_id
    FROM orders o
    JOIN customer_first_order c ON o.customer_id = c.customer_id
),
cohort_sizes AS (
    SELECT cohort_month, COUNT(DISTINCT customer_id) AS total_cohort_size
    FROM customer_first_order
    GROUP BY cohort_month
)
SELECT
    a.cohort_month,
    s.total_cohort_size,
    a.month_number,
    COUNT(DISTINCT a.customer_id) AS active_customers,
    ROUND(
        COUNT(DISTINCT a.customer_id)::NUMERIC / s.total_cohort_size * 100, 2
    ) AS retention_rate_pct
FROM customer_activity a
JOIN cohort_sizes s ON a.cohort_month = s.cohort_month
GROUP BY a.cohort_month, s.total_cohort_size, a.month_number
ORDER BY a.cohort_month DESC, a.month_number ASC;
```

---

## 📊 Recommended Visualization
* **Heatmap Matrix**: Cohort months on the Y-axis, Retention Month Index (M0, M1, M2...) on X-axis with color intensity reflecting retention %.
* **Line Chart**: Overlaid cohort retention curves to visually verify if newer cohorts are flattening at higher retention levels than older cohorts.

---

## 💡 Executive Recommendation Framework
* If **Retention Curve hits 0%**: Product lacks long-term value retention; spending marketing funds on acquisition is throwing money into a leaky bucket!
* If **Retention Curve flattens above 20%**: Product has achieved stable retention; clear signal to scale paid customer acquisition.
