# Analytical Playbook — Root-Cause Analysis & Variance Isolation

> **Standard operating playbook for isolating root drivers behind metric spikes, drops, or unexpected variances.**

---

## 🎯 When to Use This Playbook
Use this playbook when a critical KPI (e.g., Conversion Rate, Daily Active Users, Net Revenue) exhibits a sudden, unexpected drop or spike that needs immediate explanation for executive leadership.

---

## ❓ Core Business Questions
1. Is the observed variance statistically real or a data pipeline logging glitch?
2. Is the variance driven by an internal operational change (e.g., code deployment, pricing update, bug) or an external market shift?
3. Which single dimension (Geographic Region, Device OS, Marketing Source, Product SKU) accounts for the majority of the variance?

---

## 🔍 The 5-Step Isolation Protocol

```text
STEP 1: Verify Data Pipeline Integrity (Check for missing logs, pipeline lag, or double counting)
        ↓
STEP 2: Decompose Metric Mathematically (Isolate numerator vs denominator changes)
        ↓
STEP 3: Segment Across Dimensions (Country, Device, Channel, User Cohort)
        ↓
STEP 4: Cross-Reference Internal Events (Check product deployments, marketing campaigns, outages)
        ↓
STEP 5: Quantify Contribution % of Each Factor
```

---

## 💻 SQL Query Pattern (Variance Contribution % Isolation)

```sql
WITH metric_periods AS (
    SELECT
        device_category,
        SUM(CASE WHEN order_date BETWEEN '2026-08-01' AND '2026-08-07' THEN net_amount ELSE 0 END) AS baseline_revenue,
        SUM(CASE WHEN order_date BETWEEN '2026-08-08' AND '2026-08-14' THEN net_amount ELSE 0 END) AS current_revenue
    FROM orders
    GROUP BY device_category
),
variance_calc AS (
    SELECT
        device_category,
        baseline_revenue,
        current_revenue,
        (current_revenue - baseline_revenue) AS absolute_variance,
        SUM(current_revenue - baseline_revenue) OVER () AS total_system_variance
    FROM metric_periods
)
SELECT
    device_category,
    baseline_revenue,
    current_revenue,
    absolute_variance,
    -- Calculate contribution percentage of this specific dimension to total variance
    ROUND(
        absolute_variance / NULLIF(total_system_variance, 0) * 100, 2
    ) AS variance_contribution_pct
FROM variance_calc
ORDER BY ABS(absolute_variance) DESC;
```

---

## 💡 Executive Memo Template for Root-Cause Findings

```text
EXECUTIVE MEMO: Q3 Mobile Revenue Drop Root Cause
------------------------------------------------
1. WHAT HAPPENED: Total weekly revenue dropped by \$45,000 (-12%) during the week of Aug 8th.
2. ROOT CAUSE: 88% of the total dollar variance was isolated to iOS Mobile users following App Version 4.2 release.
3. WHY IT HAPPENED: App Version 4.2 introduced a bug where Apple Pay checkout buttons failed to render on iOS 17 devices.
4. ACTION TAKEN: Engineering released hotfix Version 4.2.1 on Aug 12th; conversion rates restored to baseline within 4 hours.
```
