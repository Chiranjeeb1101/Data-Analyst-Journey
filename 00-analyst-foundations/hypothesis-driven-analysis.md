# Hypothesis-Driven Analysis

> **Avoiding endless exploratory "data fishing" by testing structured, business-grounded hypotheses.**

---

## 🎯 Why Hypothesis-Driven Analysis Matters

Unstructured exploration leads to:
* Wasted hours querying unrelated tables.
* Spurious correlations (confounding correlation with causation).
* Generic dashboards that fail to drive business action.

Hypothesis-driven analysis guarantees that every SQL query or chart directly tests a specific commercial explanation.

---

## 📝 The Hypothesis Structure

A complete analytical hypothesis must contain 3 elements:

```text
[SPECIFIC EVENT / DRIVER] + [EXPECTED MECHANISM] + [MEASURABLE METRIC IMPACT]
```

### Good vs. Bad Hypothesis Examples

* ❌ **Bad**: *"Maybe users aren't buying because the site is slow or bad."* (Vague, unmeasurable)
* ✅ **Good**: *"The 15% drop in checkout conversion rate for mobile users in August is driven by page load delays (>3s) on payment gateway integration, increasing mobile cart abandonment."*

---

## 🧪 The Hypothesis Testing Matrix

| Hypothesis | Data Required | Test / Query | Falsification Criteria | Decision Action |
| :--- | :--- | :--- | :--- | :--- |
| Mobile latency caused checkout drop | `page_logs`, `checkout_events` | Segment checkout conversion by mobile vs desktop across page load speed buckets | Mobile conversion is flat across latency buckets | If validated: Escalate latency bug to Mobile Product Team |
| Price increase reduced repeat purchase rate | `orders`, `customer_cohorts` | Compare 30-day repeat purchase rate for cohorts pre- vs post-price change | Repeat rate is equal or higher post-price increase | If validated: Re-evaluate tier-1 pricing structure |
