# Analytical Hypothesis Document — [Feature / Issue Name]

**Analyst**: [Your Name]  
**Stakeholder**: [Name / Role]  
**Date**: [YYYY-MM-DD]

---

## 1. Problem Statement & Baseline Metric
* **Symptom / Problem**: [e.g., Q3 Mobile Checkout Conversion dropped by 3.2 percentage points]
* **Baseline Metric**: [e.g., Conversion was 14.5% in Q2, now 11.3% in Q3]

---

## 2. Formulated Hypotheses

| # | Hypothesis Statement | Proposed Mechanism | Required Data | Falsification Metric |
| :--- | :--- | :--- | :--- | :--- |
| **H1** | Mobile checkout drop is driven by latency spikes in the new iOS payment SDK. | Latency > 3s causes cart abandonment on payment step. | `page_logs`, `checkout_events` | Mobile conversion rate is uniform across page load speed tiers. |
| **H2** | Higher shipping charges introduced in July led to abandonment among low-order-value buyers. | Shipping fee > 15% of cart value decreases conversion. | `orders`, `shipping_fees` | Conversion drop is equal across high- and low-cart-value tiers. |

---

## 3. Experimental / Analytical Plan
* **SQL Queries**: Location of validation scripts in `/notebooks/` or `/03-sql/`.
* **Segmentation**: Slice metrics by Device OS, Order Value Bucket, Geography, and Acquisition Channel.

---

## 4. Findings & Decision Matrix

| Hypothesis | Status (Validated / Rejected) | Empirical Evidence | Recommended Action |
| :--- | :--- | :--- | :--- |
| **H1** | 🟢 **Validated** | iOS users experiencing >3s page loads convert at 4.1% vs 14.2% for <1s loads. | Escalate iOS payment SDK lag to Engineering. |
| **H2** | 🔴 **Rejected** | Low-order-value conversion remained steady at 12.1%. | No change to shipping fee structure needed. |
