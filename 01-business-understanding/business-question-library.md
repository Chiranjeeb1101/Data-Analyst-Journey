# Master Business Question Library Across Domains

> **A comprehensive library of real-world business problems, analytical sub-questions, and domain KPIs across key industry sectors.**

---   

## 🛒 1. E-Commerce Domain

### Core Business Goal: Maximize Lifetime Gross Margin & Purchase Frequency

| Business Challenge | Analytical Sub-Questions | Primary KPIs | Key Data Sources |
| :--- | :--- | :--- | :--- |
| **High Cart Abandonment Rate** | 1. At which specific step in the checkout funnel does drop-off peak?<br>2. Does drop-off vary by payment method or shipping tier?<br>3. Are high cart values (> \$150) abandoning at higher rates? | Checkout Conversion Rate, Cart Abandonment Rate, Step Drop-off % | `cart_events`, `checkout_logs`, `shipping_options` |
| **Declining Customer Lifetime Value (LTV)** | 1. Are 60-day repeat purchase rates dropping across recent acquisition cohorts?<br>2. Is Average Order Value (AOV) declining due to discounting?<br>3. Which product categories yield the highest repeat rate? | 30/60/90-Day LTV, Repeat Purchase Rate, AOV | `orders`, `order_items`, `customers`, `coupons` |

---

## 💼 2. SaaS (Software as a Service) Domain

### Core Business Goal: Drive Recurring Revenue Retention & Net Expansion

| Business Challenge | Analytical Sub-Questions | Primary KPIs | Key Data Sources |
| :--- | :--- | :--- | :--- |
| **Rising Monthly Churn Rate** | 1. Are user accounts exhibiting declining daily active usage prior to cancellation?<br>2. Is churn concentrated in a specific subscription tier or billing frequency (Monthly vs Annual)?<br>3. Which product features correlate with 90-day retention? | Net Revenue Retention (NRR), Logo Churn %, Monthly Recurring Revenue (MRR) | `subscriptions`, `billing_history`, `feature_logs` |
| **Trial Conversion Bottleneck** | 1. What percentage of trial users complete the core onboarding activation flow?<br>2. What is the average time to first value (TTFV) for converted vs non-converted trials? | Free-to-Paid Conversion %, Activation Rate, TTFV | `user_events`, `trial_accounts`, `invoices` |

---

## 📦 3. Logistics & Supply Chain Domain

### Core Business Goal: Optimize On-Time Delivery & Reduce Fulfillment Operating Costs

| Business Challenge | Analytical Sub-Questions | Primary KPIs | Key Data Sources |
| :--- | :--- | :--- | :--- |
| **Delayed Order Shipments** | 1. Which fulfillment centers experience the highest processing backlog?<br>2. What is the variance between estimated vs actual transit times across carriers?<br>3. How do stock-outs impact order fulfillment SLA adherence? | On-Time Delivery Rate (OTD), Order Lead Time, Fulfillment SLA Adherence % | `shipments`, `warehouse_logs`, `carriers`, `inventory` |
