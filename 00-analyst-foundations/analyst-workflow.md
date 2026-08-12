# The Professional Data Analyst Workflow

> **The end-to-end operational framework for conducting rigorous, repeatable, high-impact business analysis.**

---

## 🔄 The 7-Stage Analyst Execution Lifecycle

```text
1. BUSINESS UNDERSTANDING & PROBLEM FRAMING
        ↓
2. HYPOTHESIS FORMULATION
        ↓
3. DATA RECONNAISSANCE & QUALITY AUDIT
        ↓
4. DATA EXTRACTION & MANIPULATION (SQL / Pandas / Excel)
        ↓
5. RIGOROUS ANALYSIS (EDA, Cohort, Funnel, Stats)
        ↓
6. INSIGHT SYNTHESIS & STORYTELLING
        ↓
7. RECOMMENDATION & STAKEHOLDER DECISION
```

---

## 📋 Breakdown of Stages

### Stage 1: Business Framing & Stakeholder Alignment
* Identify the target stakeholder (e.g., VP of Sales, Head of Product).
* Clarify the underlying business decision: *What action will be taken based on the output?*

### Stage 2: Hypothesis Formulation
* Draft explicit, falsifiable hypotheses prior to querying:
  *Example*: *"User drop-off at checkout step 2 is caused by unexpected shipping cost additions, affecting high-cart-value users."*

### Stage 3: Data Reconnaissance & Quality Audit
* Locate exact tables and verify **table grain** (*What does one row represent?*).
* Perform data sanity checks (check for duplicates, NULL values, impossible dates, outlier spikes).

### Stage 4: Extraction & Manipulation
* Write clean SQL CTEs or Pandas workflows. Validate row counts after JOIN operations.

### Stage 5: Rigorous Analysis
* Break down overall metrics across customer segments, time cohorts, geography, and acquisition channels.
* Differentiate correlation from true causal drivers.

### Stage 6: Insight Synthesis & Storytelling
* Format findings using the **5 Core Analytical Questions**:
  1. What happened?
  2. Why did it happen?
  3. Why does it matter?
  4. What should we do?
  5. What happens if we do nothing?

### Stage 7: Action & Tracking
* Present actionable recommendations with trade-offs. Track business outcomes post-implementation.
