# Analytical Playbook — Funnel Conversion Analysis

> **Standard operating playbook for identifying drop-offs, conversion rates, and friction points across multi-step user flows.**

---

## 🎯 When to Use This Playbook
Use this playbook when optimizing conversion flows (e.g., Checkout Funnel, User Onboarding Flow, Lead-to-Sale Sales Pipeline, Feature Activation).

---

## ❓ Core Business Questions
1. What is the overall end-to-end conversion rate of the funnel?
2. Which specific step experiences the largest absolute and percentage drop-off?
3. How does conversion performance vary across user device types, channels, or regional demographics?

---

## 💻 SQL Query Pattern (PostgreSQL / Snowflake / BigQuery)

```sql
WITH user_funnel_steps AS (
    SELECT
        user_id,
        MAX(CASE WHEN event_name = 'landing_page_view' THEN 1 ELSE 0 END) AS step_1_viewed,
        MAX(CASE WHEN event_name = 'product_added_to_cart' THEN 1 ELSE 0 END) AS step_2_carted,
        MAX(CASE WHEN event_name = 'checkout_initiated' THEN 1 ELSE 0 END) AS step_3_checkout,
        MAX(CASE WHEN event_name = 'payment_completed' THEN 1 ELSE 0 END) AS step_4_purchased
    FROM user_event_logs
    WHERE event_date BETWEEN '2026-08-01' AND '2026-08-31'
    GROUP BY user_id
)
SELECT
    SUM(step_1_viewed) AS step_1_users,
    SUM(step_2_carted) AS step_2_users,
    SUM(step_3_checkout) AS step_3_users,
    SUM(step_4_purchased) AS step_4_users,
    -- Step-to-Step Conversion Rates
    ROUND(SUM(step_2_carted)::NUMERIC / NULLIF(SUM(step_1_viewed), 0) * 100, 2) AS conversion_step_1_to_2_pct,
    ROUND(SUM(step_3_checkout)::NUMERIC / NULLIF(SUM(step_2_carted), 0) * 100, 2) AS conversion_step_2_to_3_pct,
    ROUND(SUM(step_4_purchased)::NUMERIC / NULLIF(SUM(step_3_checkout), 0) * 100, 2) AS conversion_step_3_to_4_pct,
    -- Overall End-to-End Conversion Rate
    ROUND(SUM(step_4_purchased)::NUMERIC / NULLIF(SUM(step_1_viewed), 0) * 100, 2) AS overall_funnel_conversion_pct
FROM user_funnel_steps;
```

---

## 📊 Recommended Visualization
* **Funnel Chart / Horizontal Bar Chart**: Visually depicting user volume shrinking across sequential steps, annotated with step-to-step drop-off percentages.

---

## 💡 Executive Recommendation Framework
* **Focus Engineering & Product efforts on the step with the highest relative drop-off**: Fixing a 40% drop-off between Cart → Checkout yields far greater financial return than optimizing the Landing → Cart step!
