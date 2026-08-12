# [Project Name] — End-to-End Business Data Analysis

## 🎯 Executive Summary & Impact

A comprehensive business data analysis solving **[Core Business Problem]** for **[Industry / Domain, e.g., SaaS / E-Commerce]**.

* **Key Outcome**: Identified \$120k annual revenue leakage in user subscription renewals and delivered a decision-ready executive strategy.
* **Core Technical Stack**: Advanced SQL (CTEs, Window Functions), Python / Pandas (Data Cleaning & Time-Series), Power BI (DAX Star Schema Dashboard), Data Storytelling.

---

## 📁 Project Structure

```text
├── README.md                           # Project documentation & summary
├── data/
│   ├── raw/                            # Raw source datasets
│   └── processed/                      # Cleaned, aggregated datasets
├── sql/
│   ├── 01_data_audit_and_cleaning.sql   # Data quality checks & grain validation
│   ├── 02_cohort_retention_analysis.sql # Retention CTEs & window queries
│   └── 03_rfm_customer_segmentation.sql# RFM scoring & segmentation queries
├── notebooks/
│   └── 01_exploratory_data_analysis.ipynb# Python Pandas analysis & statistical checks
├── dashboards/
│   └── executive_dashboard.pbix        # Interactive Power BI dashboard file
└── report/
    └── executive_memo.md               # 5-Question executive analytical briefing
```

---

## 📊 Business Problem & Analytical Approach

### 1. Business Framing
* **Stakeholder**: VP of Growth & Revenue Operations.
* **Core Question**: *"Why are customer churn rates increasing among 6-month subscribers, and how can we reverse the trend?"*

### 2. Analytical Methodology
1. **Grain Definition**: Table grain established at `one row per monthly subscription billing event`.
2. **Cohort Retention Analysis**: Grouped users by signup month and tracked retention at M1, M3, M6, and M12.
3. **Driver Isolation**: Sliced churn across payment failure, active feature usage frequency, and customer support ticket volume.
4. **RFM Segmentation**: Classified user base into Champions, At-Risk, and Churned segments.

---

## 📈 Key Findings & Insights

### 1. Involuntary Churn Drives 42% of Subscription Loss
* **Data**: 42% of account cancellations were caused by unhandled payment gateway declines (expired credit cards), not active user cancellation.
* **Impact**: Recapturable revenue of ~\$50,000 annually.

### 2. Low Feature Activation Predicts Churn at Month 4
* **Data**: Users who perform fewer than 3 team collaborations during their first 14 days exhibit an 82% churn rate by Month 6.

---

## 🚀 Strategic Recommendations & Action Plan

1. **Implement Automated Dunning & Account Updating**: Deploy automated payment retries and card updater API, reducing involuntary churn by an estimated 25%.
2. **Redesign Trial Onboarding for Team Activation**: Trigger in-app prompt guiding users to invite team members within 48 hours of signup.

---

## 🛠 How to Reproduce Analysis

1. Clone repository and navigate to project folder:
   ```bash
   git clone https://github.com/user/data-analyst-journey.git
   cd data-analyst-journey/19-projects/flagship/
   ```
2. Execute SQL scripts in `/sql/` against BigQuery / Snowflake / PostgreSQL.
3. Run Python notebook in `/notebooks/`:
   ```bash
   jupyter notebook notebooks/01_exploratory_data_analysis.ipynb
   ```
4. Open `dashboards/executive_dashboard.pbix` in Power BI Desktop to inspect DAX measures.
