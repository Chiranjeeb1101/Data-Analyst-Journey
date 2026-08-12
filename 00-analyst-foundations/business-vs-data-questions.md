# Business Questions vs. Data Questions

> **How to translate vague, open-ended business requests into precise, quantitative data queries.**

---

## 🎯 The Translation Challenge

Stakeholders speak in **business outcomes, pain points, and commercial goals**.  
Data systems store **raw transactions, events, timestamps, and relational records**.

An elite analyst acts as a bi-directional translator.

---

## 🔄 Translation Matrix & Examples

| Vague Business Question | Stakeholder Intent | Quantitative Data Questions | Required Data & Tables |
| :--- | :--- | :--- | :--- |
| *"Why are sales dropping?"* | Need to stop revenue loss and find fix | 1. Is revenue drop driven by lower order volume or lower Average Order Value (AOV)?<br>2. Are new or returning customer cohorts dropping?<br>3. Which product category or region accounts for the variance? | `orders`, `order_items`, `customers`, `products` |
| *"Is our marketing campaign working?"* | Decide whether to reallocate ad budget | 1. What is the Customer Acquisition Cost (CAC) by channel?<br>2. What is the 30-day and 90-day LTV for users acquired via Campaign X vs Control?<br>3. What is the return on ad spend (ROAS)? | `marketing_spend`, `user_signups`, `user_orders` |
| *"Are users liking our new app feature?"* | Decide whether to keep, iterate, or remove feature | 1. What is the feature adoption rate among active users?<br>2. Does feature usage correlate with 30-day user retention?<br>3. What is the task completion rate and drop-off in feature funnel? | `app_events`, `user_sessions`, `user_retention` |

---

## 🛠 The Translation Protocol

1. **Clarify Scope**: *"When you say sales are dropping, over what time period are we comparing (MoM, YoY)?"*
2. **Identify Decision**: *"If we find channel X is underperforming, are we able to reallocate spend immediately?"*
3. **Deconstruct Metrics**: Break the business metric down into its mathematical components:
   $$\text{Revenue} = \text{Active Users} \times \text{Purchase Frequency} \times \text{Average Order Value}$$
4. **Formulate Data Queries**: Query each sub-component to isolate the driver of change.
