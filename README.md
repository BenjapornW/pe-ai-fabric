# 💸 Portview 

## 🔗 Table of Contents
1. [About the Project](#about-the-project)
2. [Problem Statement](#problem-statement)
3. [Technology Stack](#technology-stack)
4. [Data Architecture](#data-architecture)
5. [Components](#components)
6. [Impact](#impact)
7. [Key Takeaways](#key-takeaways)
8. Gold Layer Star Schema
9. Key KPIs
10. [Power BI Dashboard](#power-bi-dashboard)


## 🔭 About the Project
Portview, an end-to-end Microsoft Fabric solution that automates private equity portfolio reporting and embeds AI to accelerate research, analysis, and investor communications.

What is a private equity?
Private equity (PE) is an investment business where firms buy whole companies, improve them, and sell them later for a profit. Unlike public stocks, these companies are not traded on open stock exchanges.

<img src="https://napkinfinance.com/wp-content/uploads/2018/01/NapkinFinance-PrivateEquity-Napkin-09-08-20-v05.jpg" width="460" height="460" alt="Private Equity Explained">


## 🚩 Problem Statement
Many private equity firms rely on multiple Excel spreadsheets to track performance, making reporting slow, difficult to manage, and prone to errors. This often leads to inconsistent numbers, limited visibility, and delays in decision-making.
To address these challenges, an automated dashboard brings all key information into one place, providing a single source of truth and real-time visibility into performance. This helps teams spend less time preparing reports and more time making informed decisions.


## 🛠 Technology Stack
- Fabric
- Power BI
- Microsoft Copilot

## 📦 Data Architecture
- Medallion Architecture

We adopted the Medallion Architecture (Bronze → Silver → Gold) in Microsoft Fabric to bring structure and reliability to a data environment that is inherently messy. Private equity data arrives from many sources, each with different formats and quality levels.
Bronze is the raw landing zone. Every record arrives exactly as the source sent it, nothing transformed or discarded.
Silver is where data becomes trustworthy. Records are cleaned, standardised across portfolio companies, and validated before anything reaches a dashboard.
Gold contains only business-ready metrics — EBITDA, IRR — consistent and ready for Power BI, Excel, or reporting.
The practical benefit is auditability. When a user questions a return figure, we can trace it from the dashboard all the way back to the original source document.

![PrivateEquityMedallion](https://github.com/BenjapornW/pe-ai-fabric/blob/main/img/pefabricdiagram.png)


## 🧩 Components

1. Data Sources
- Files – CSV, Excel, and flat files.
- Databases – Operational and transactional systems.
- APIs – External applications and third-party data sources.

2. Data Integration & Transformation
- Data Pipeline – Automates data ingestion into Microsoft Fabric.
- Bronze Layer – Stores raw source data.
- Dataflow Gen2 – Cleanses and standardizes data.
- Silver Layer – Stores validated and transformed data.
- Notebooks – Performs advanced data transformations.
- Gold Layer – Creates business-ready datasets.
- SQL Endpoint / Data Warehouse – Enables SQL-based analytics and reporting.
- Semantic Model – Provides centralized business metrics and KPIs.

3. Visualization
- Power BI – Connects to the Semantic Model to deliver interactive dashboards, reports, and performance insights.

4. AI-Powered Insights
- Copilot AI Agent – Generates executive summaries, explains performance trends, highlights key insights, and recommends actions based on dashboard data.

## 🎯 Impact
- Replaced manual, Excel-based reporting with an automated daily pipeline, freeing the team for higher-value work.
- Single shared semantic model eliminates version conflicts and ensures everyone works from the same numbers.
- Near real-time portfolio visibility replaces monthly retrospectives, enabling faster and more informed decisions.
- Embedded AI assists with research, memo drafting, and variance commentary without unnecessary cost overhead.
- Full data lineage means every metric is traceable back to its source, which is critical for regulatory reporting.

## 💡 Key Takeaways
- A trusted data foundation must come before AI. Automation only adds value when the underlying numbers are reliable.
- Medallion Architecture suits PE data well. It handles inconsistent multi-source inputs while maintaining auditability.
- A shared semantic model creates team alignment and removes the risks that come with spreadsheet-based workflows.
- BI capabilities are most impactful when built around the firm's value creation objectives, not just data availability.

## 📝 Gold Layer Star Schema
| Table | Type | Description |
| -------- | -------- | -------- |
| fact_fund_performance  | Fact   | Tracks fund-level growth and investor returns using IRR and MOIC.  |
| fact_portfolio_company_financials | Fact   | Tracks company-level operating profits and revenue using EBITDA.  |
| dim_fund_family   | Dimension   | Stores the parent private equity firm name, scale, and headquarters.   |
| dim_fund  | Dimension   | Stores the specific fund name, starting year, and investment strategy.  |
| dim_portfolio_company | Dimension   | Stores the acquired company name, industry sector, and country location.   |
| dim_date| Dimension   | Stores calendar details to standardise quarterly and yearly time tracking. |

## Key KPIs
- EBITDA (Earnings Before Interest, Taxes, Depreciation, and Amortization)
- IRR (Internal Rate of Return) 
- MOIC (Multiple on Invested Capital)

## 🧪 Data Validation
Tested with PySpark native checks:

- ✅ No zero IRR


## ![Power Bi](https://img.shields.io/badge/power_bi-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)

## Genrative AI Application - Microsoft Copilot
- Summarise report by using a smart narrative

- Create report subscriptions with Copilot summaries

- Suggest decision/action

- Integrate with other Copilots



