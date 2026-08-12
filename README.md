<div align="center">

# 📊 Elite Data Analyst Journey

### *A Lifelong Architecture for Master-Level Business Analytics, Data Problem Solving & Executive Decision Making*

[![Focus](https://img.shields.io/badge/Domain-Business_Analytics-007ACC?style=for-the-badge&logo=googleanalytics&logoColor=white)](#)
[![SQL](https://img.shields.io/badge/SQL-Window_Functions_%26_CTEs-E38C00?style=for-the-badge&logo=postgresql&logoColor=white)](#)
[![Python](https://img.shields.io/badge/Python-Pandas_%26_Scripting-3776AB?style=for-the-badge&logo=python&logoColor=white)](#)
[![Power BI](https://img.shields.io/badge/Power_BI-DAX_%26_Star_Schema-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](#)
[![Excel](https://img.shields.io/badge/Excel-Advanced_Modeling-1F7244?style=for-the-badge&logo=microsoftexcel&logoColor=white)](#)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](#)

---

[Core Philosophy](#-core-philosophy) • [Capability Stack](#-the-21-layer-capability-stack) • [Repository Directory](#-repository-navigation-directory) • [Playbooks & Templates](#-analytical-playbooks--templates) • [Recruiter & Manager Guide](#-guide-for-hiring-managers--recruiters)

---

</div>

## 📌 Mission Statement

This repository is an **intentionally dedicated architecture focused 100% on becoming an exceptionally strong Data Analyst**.

It strictly excludes generic Data Science, Machine Learning algorithms, Software Engineering frameworks, or Data Engineering pipelines.

The goal is to develop the complete skill set required to become a **top-level, high-impact Data Analyst** who can independently turn vague, ambiguous business problems into empirical, decision-ready solutions that drive revenue growth, cost optimization, and strategic clarity.

---

## 🧭 Core Philosophy: Business-First Analytics

```text
  ┌────────────────────────┐      ┌────────────────────────┐      ┌────────────────────────┐
  │   BUSINESS PROBLEM     │ ───► │  HYPOTHESIS & FRAMING  │ ───► │  DATA RECONNAISSANCE   │
  │ (Vague Request / Goal) │      │ (MECE Tree / Sub-Qs)   │      │ (Table Grain & Quality)│
  └────────────────────────┘      └────────────────────────┘      └────────────────────────┘
                                                                               │
  ┌────────────────────────┐      ┌────────────────────────┐                   │
  │   BUSINESS DECISION    │ ◄─── │  EXECUTIVE NARRATIVE   │ ◄─────────────────┘
  │ (Revenue / Cost Impact)│      │ (What, Why, Action)    │   (SQL / Pandas / DAX)
  └────────────────────────┘      └────────────────────────┘
```

> **The No-Tutorial-Dump Rule**: Every topic, query, and analysis in this repository must directly satisfy one question:  
> **"Does this improve my ability to solve a real business problem using data?"**

---

## 🗺 Quick Navigation: Strategy & System Files

| Document | Description | Purpose |
| :--- | :--- | :--- |
| 📜 [**Analyst Manifesto**](./analyst-manifesto.md) | Core Mindset & Principles | The non-negotiable rules of elite analytical rigor and business-first thinking. |
| 🗺️ [**Career Roadmap**](./career-roadmap.md) | Stage-by-Stage Progression | Career trajectory from Foundational Analyst to Principal Analyst & BI Lead. |
| 📊 [**Skills Matrix**](./skills-matrix.md) | Self-Evaluation Rubric | 5-tier competency rating across SQL, Excel, Python, Stats, DAX, and Storytelling. |
| 🔄 [**Learning System**](./learning-system.md) | Daily & Weekly Cadence | The lifelong operational loop for continuous practice and evidence generation. |
| 📈 [**Progress Log**](./progress-log.md) | Milestone Tracker | Log for the initial 100-day structured phase and ongoing lifelong achievements. |
| 📖 [**Core Glossary**](./glossary.md) | Terminology Index | Vetted definitions of unit economics, business KPIs, statistical metrics, and SQL terms. |
| 📚 [**Resource Library**](./resources.md) | Reading & Data Sources | High-signal books, articles, documentation, and open-source analytical datasets. |

---

## 📂 Repository Navigation Directory

This repository is organized into **21 core capability modules**, supporting dataset directories, and standardized analytical playbooks:

### 🏛️ Foundational & Business Understanding Modules

| Module Directory | Primary Focus | Key Skills & Artifacts |
| :--- | :--- | :--- |
| 📁 [**`00-analyst-foundations/`**](./00-analyst-foundations/) | Analytical Mindset & Problem Framing | [Workflow](./00-analyst-foundations/analyst-workflow.md), [Question Translation](./00-analyst-foundations/business-vs-data-questions.md), [Hypothesis Framing](./00-analyst-foundations/hypothesis-driven-analysis.md), [Table Grain](./00-analyst-foundations/dimensions-vs-measures.md) |
| 📁 [**`01-business-understanding/`**](./01-business-understanding/) | Business Models & Unit Economics | Revenue Models, Cost Structures, [Master Business Question Library](./01-business-understanding/business-question-library.md) |

### 🛠️ Core Technical Execution Modules

| Module Directory | Primary Focus | Key Skills & Artifacts |
| :--- | :--- | :--- |
| 📁 [**`02-excel/`**](./02-excel/) | Advanced Modeling & Automation | XLOOKUP, Dynamic Arrays (`FILTER`/`UNIQUE`), Pivot Tables, Power Query transformations |
| 📁 [**`03-sql/`**](./03-sql/) | Production SQL Mastery | Window Functions (`ROW_NUMBER`, `LAG`/`LEAD`), CTEs, Aggregations, Query Optimization |
| 📁 [**`04-python/`**](./04-python/) | Analytical Scripting | Automation, File Processing, API Ingestion, Reproducible Scripting |
| 📁 [**`05-pandas/`**](./05-pandas/) | Data Manipulation Pipeline | `Load → Inspect → Clean → Transform → Analyze → Validate → Communicate` |
| 📁 [**`06-statistics/`**](./06-statistics/) | Applied Business Statistics | Descriptive Stats, Distributions, Confidence Intervals, Hypothesis Testing, Regression |
| 📁 [**`07-data-cleaning/`**](./07-data-cleaning/) | Data Quality & Anomaly Audit | Missingness Audit, Duplicates, Data Type Drift, Outliers, Anomaly Detection |
| 📁 [**`08-data-modeling/`**](./08-data-modeling/) | Dimensional Modeling | Star Schema Architecture, Fact vs. Dimension Tables, Table Grain Enforcement |

### 📈 Domain Analytics, Methodologies & BI Modules

| Module Directory | Primary Focus | Key Skills & Artifacts |
| :--- | :--- | :--- |
| 📁 [**`09-kpi-metrics/`**](./09-kpi-metrics/) | Metric Engineering & Architecture | Metric Trees, Metric Dictionaries, Leading vs. Lagging Indicator Mapping |
| 📁 [**`10-exploratory-analysis/`**](./10-exploratory-analysis/) | Exploratory Data Analysis (EDA) | Univariate, Bivariate & Multivariate EDA, Distribution Trends, Anomaly Spotting |
| 📁 [**`11-advanced-analytics/`**](./11-advanced-analytics/) | High-Impact Analytics | Cohort Analysis, Funnel Conversion, Retention Curves, RFM Segmentation, Root-Cause |
| 📁 [**`12-experimentation/`**](./12-experimentation/) | A/B Testing & Hypothesis Evaluation | Sample Size Calculation, Significance Testing, Effect Size, Business Decision Matrix |
| 📁 [**`13-forecasting/`**](./13-forecasting/) | Time Series & Business Projection | Moving Averages, Seasonality Adjustment, Trend Models, Uncertainty Boundaries |
| 📁 [**`14-data-visualization/`**](./14-data-visualization/) | Visual Design & Hierarchy | Chart Selection Matrix, Visual Cognitive Load, Executive Presentation Standards |
| 📁 [**`15-powerbi/`**](./15-powerbi/) | Power BI & DAX Mastery | Star Schema Modeling, DAX Measures, Time-Intelligence, Executive UX |
| 📁 [**`16-data-storytelling/`**](./16-data-storytelling/) | Strategic Communication | Insight Writing, Executive Memos, 5-Question Framework (*What, Why, Action*) |
| 📁 [**`17-business-domains/`**](./17-business-domains/) | Domain Analytics Playbooks | E-Commerce, SaaS, Logistics, Marketing, Finance, Sales, Product, Operations |

### 💼 Portfolio Projects, Case Studies & Playbooks

| Directory | Content Type | Highlights |
| :--- | :--- | :--- |
| ⚡ [**`20-analytical-patterns/`**](./20-analytical-patterns/) | Reusable Playbooks | [Revenue](./20-analytical-patterns/revenue-analysis.md), [Retention](./20-analytical-patterns/retention-analysis.md), [Funnel](./20-analytical-patterns/funnel-analysis.md), [RFM Segmentation](./20-analytical-patterns/customer-segmentation.md), [Root-Cause](./20-analytical-patterns/root-cause-analysis.md) |
| 📑 [**`templates/`**](./templates/) | Standardized Document Templates | [Executive Report](./templates/analytical-report-template.md), [Data Dictionary](./templates/data-dictionary-template.md), [Hypothesis Doc](./templates/hypothesis-document-template.md), [Project README](./templates/project-readme-template.md) |
| 🔬 [**`18-case-studies/`**](./18-case-studies/) | Real Business Problem Walkthroughs | End-to-end case investigations starting from business problems to recommendations |
| 🚀 [**`19-projects/`**](./19-projects/) | Production Portfolio Projects | Mini, Intermediate, Advanced, and Flagship analytics projects |
| 📊 [`dashboards/`](./dashboards/) & [`notebooks/`](./notebooks/) | BI & Code Assets | Interactive Power BI files (.pbix), Excel workbooks, and Jupyter Notebooks |

---

## ⚡ Analytical Playbooks & Templates

The repository includes production-ready analytical playbooks containing formulas, SQL CTE queries, Pandas scripts, and executive decision frameworks:

```text
20-analytical-patterns/
├── revenue-analysis.md           # Net Revenue decomposition & driver isolation
├── retention-analysis.md         # Cohort N-month retention SQL queries & heatmaps
├── funnel-analysis.md            # Multi-step drop-off conversion rate queries
├── customer-segmentation.md      # RFM scoring window functions & strategy matrix
└── root-cause-analysis.md        # 5-step isolation protocol & variance contribution %
```

---

## 🎯 Guide for Hiring Managers & Recruiters

If you are evaluating this repository for a **Data Analyst, Senior Analyst, Analytics Lead, or BI Lead** role, please note:

1. **Business Impact Over Vanity Code**: Projects in [`18-case-studies/`](./18-case-studies/) and [`19-projects/`](./19-projects/) begin with business questions and end with financial/operational recommendations.
2. **Production-Grade SQL**: Queries in [`03-sql/`](./03-sql/) and [`20-analytical-patterns/`](./20-analytical-patterns/) use clean CTEs, window functions (`LAG`/`LEAD`, `NTILE`), aggregations, and strict join-grain validation.
3. **Data Quality Rigor**: Every analysis enforces table grain validation and documents data quality constraints before drawing conclusions.
4. **Executive Communication**: Reports follow standardized structures in [`templates/analytical-report-template.md`](./templates/analytical-report-template.md) answering: *What happened? Why did it happen? Why does it matter? What should we do?*

---

## 🏆 The Ultimate Analyst Benchmark

The standard of this repository is not merely knowing SQL syntax or building pretty charts.

The standard is:

> **"Give me an ambiguous business problem, and I can independently turn it into a reliable, empirical, decision-ready analysis that drives measurable business value."**

---

<div align="center">

⭐ **Created for continuous lifelong growth in Data Analysis.**  
*Continuous Learning • Empirical Rigor • Business Impact*

</div>
