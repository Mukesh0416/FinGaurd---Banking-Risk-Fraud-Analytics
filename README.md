
# Banking Risk & Fraud Analytics

## Bank Transaction Fraud Risk Analysis

An end-to-end banking transaction risk analysis project focused on identifying unusual transaction patterns, prioritizing potentially risky transactions, and communicating insights through Python, PostgreSQL, Microsoft Excel, and Power BI.

The project uses statistical, rule-based risk scoring to identify unusual transaction characteristics and support further investigation.

> **Important:** The source dataset does not contain confirmed fraud labels. Therefore, flagged transactions represent statistical anomalies requiring review, not verified fraudulent transactions.

---

## 1. Project Overview

Financial institutions process large volumes of transactions, making it challenging to manually identify unusual activity across accounts, merchants, locations, and time periods.

This project develops an analytical workflow to:

- Identify transactions with unusual financial or behavioral characteristics.
- Analyze transaction patterns across accounts, merchants, locations, and time periods.
- Develop a statistical method for flagging potential risk indicators.
- Compare findings across Python, PostgreSQL, Excel, and Power BI.
- Present actionable observations through an interactive dashboard.

### Dataset Overview

| Metric | Value |
|---|---:|
| Total Transactions | 2,512 |
| Transactions Flagged for Review | 230 |
| Flagged Transaction Rate | 9.16% |
| Transactions with Multiple Signals | 5 |

---

## 2. Project Highlights

- Analyzed and processed **2,512 banking transactions** using Python and Pandas.
- Developed an **IQR-based statistical risk scoring method** using transaction amount, login attempts, and transaction duration.
- Flagged **230 transactions (9.16%)** for further review based on implemented risk rules.
- Identified **5 transactions** that triggered two risk signals simultaneously.
- Compared headline analytical results across Python, PostgreSQL, Excel, and Power BI.
- Built an interactive dashboard containing key metrics, geographic comparisons, monthly trends, and account-level risk summaries.
- Investigated transaction-volume bias and applied rate-based comparisons to improve geographic analysis.

---

## 3. Technology Stack

| Technology | Application |
|---|---|
| Python | Data preparation, feature engineering, exploratory analysis, and statistical scoring |
| Pandas | Data manipulation, cleaning, and aggregation |
| PostgreSQL | Transaction queries, account ranking, and merchant-level analysis |
| Microsoft Excel | Pivot tables, KPI calculations, and conditional formatting |
| Power BI | Interactive reporting, visual analysis, and DAX measures |

---

## 4. Analytical Workflow

### 4.1 Data Preparation

- Imported the original banking transaction dataset.
- Checked data types, missing values, and consistency of transaction fields.
- Converted date and time fields into usable formats.
- Created additional features, including transaction hour and day of the week.
- Exported a cleaned dataset for subsequent analysis.

### 4.2 Statistical Risk Scoring

Implemented an **Interquartile Range (IQR)-based approach** to identify observations outside expected data ranges.

The scoring method examines three transaction characteristics:

1. Transaction Amount
2. Number of Login Attempts
3. Transaction Duration

Transactions triggering one or more rules are flagged for further review. The number of triggered signals is also examined to distinguish transactions with multiple unusual characteristics.

**Important:** These flags represent statistical anomalies, not confirmed fraudulent transactions. The method does not establish fraud probability or validate actual fraud outcomes.

### 4.3 Exploratory Data Analysis

Analyzed transaction distributions and compared suspicious activity across different dimensions:

- Geographic locations.
- Customer accounts.
- Merchants.
- Available time periods.

During the analysis, raw suspicious-transaction counts were found to be affected by differences in transaction volume.

Rate-normalized comparisons were therefore used to support more meaningful geographic comparisons.

### 4.4 SQL-Based Investigation

Used PostgreSQL to investigate transaction patterns and summarize potentially risky activity.

Key SQL analyses include:

- Aggregating flagged transactions by account and merchant.
- Ranking accounts according to accumulated risk indicators.
- Comparing suspicious activity across geographic groups.
- Summarizing transaction counts and relevant metrics.
- Supporting further investigation through filtered query results.

### 4.5 Excel Reporting

Created an Excel-based reporting layer using:

- Pivot tables.
- Formulas and KPI calculations.
- Conditional formatting.
- Transaction comparisons.
- Identification of records requiring additional review.

### 4.6 Power BI Dashboard

Developed an interactive dashboard to make the analysis easier to explore and communicate.

**Dashboard Components**

- KPI cards for transaction volume and flagged activity.
- Geographic comparisons of suspicious transaction rates.
- Monthly transaction trend visualizations.
- Account-level summaries highlighting repeated risk indicators.
- Interactive filters and drill-down analysis.

---

## 5. Key Findings

### 5.1 Transactions Requiring Review

A total of **230 out of 2,512 transactions (9.16%)** triggered at least one implemented risk rule.

Five transactions triggered two signals simultaneously.

These results describe the behavior of the statistical scoring rules and should not be interpreted as a confirmed fraud rate.

### 5.2 Geographic Differences

Austin, Fort Worth, and San Diego showed suspicious activity rates above the overall dataset baseline in this analysis.

Rate-based comparisons helped reduce the distortion that can occur when locations have different transaction volumes.

These findings are specific to the dataset and do not establish that the locations have higher real-world fraud rates.

### 5.3 Time-Based Patterns

Time-of-day was not a strong differentiator in the available data.

The dataset covers only a limited portion of the day, so broader conclusions about transaction timing would require more comprehensive observations.

### 5.4 Repeated Account-Level Indicators

Some accounts accumulated risk indicators across multiple transactions, even when individual transactions did not exhibit extreme values.

This suggests that account-level monitoring may complement transaction-level anomaly screening.

---

## 6. Business Recommendations

Based on the exploratory findings, the following improvements could strengthen a practical risk monitoring workflow:

- Prioritize transactions that trigger multiple independent risk indicators.
- Review accounts with repeated unusual activity across transactions.
- Compare geographic suspicious rates alongside transaction volumes.
- Reassess risk thresholds to reduce false positives caused by low-variance features.
- Introduce labeled transaction data to evaluate detection precision and recall.
- Monitor data quality and scoring performance as new transactions become available.

---

## 7. Repository Structure

```text
bank-transaction-risk-analysis/
│
├── data/
│   ├── bank_transactions_data_2.csv
│   └── fraud_data_cleaned.csv
│
├── python/
│   ├── phase2_explore.py
│   ├── phase3_cleaning.py
│   └── phase4_eda.py
│
├── sql/
│   └── fraud_analysis_queries.sql
│
├── excel/
│   └── fraud_data_cleaned.xlsx
│
├── powerbi/
│   └── dashboard.pbix
│
├── docs/
│   ├── phase1_project_planning.md
│   ├── phase8_insights.md
│   └── phase9_recommendations.md
│
└── README.md
```

---

## 8. Dataset

The project uses the publicly available **Bank Transaction Dataset for Fraud Detection** from Kaggle.

**Dataset Source:**  
[Bank Transaction Dataset for Fraud Detection – Kaggle](https://www.kaggle.com/datasets/valakhorasani/bank-transaction-dataset-for-fraud-detection)

Refer to the original dataset page for source details and applicable usage terms.

---

## 9. Limitations

- The source dataset does not provide confirmed fraud labels, so the scoring method identifies unusual observations rather than verified fraud.
- The login-attempt feature has limited variance, which can make its IQR-based rule overly sensitive.
- The available time coverage is limited, restricting the reliability of time-of-day comparisons.
- Statistical thresholds may generate false positives and require further validation.
- The reported results describe this dataset and should not be generalized to actual banking operations without additional evidence.

---

## 10. Future Enhancements

- Evaluate alternative anomaly detection methods, such as Isolation Forest.
- Tune scoring thresholds and investigate false-positive behavior.
- Incorporate labeled data to measure precision, recall, and other detection metrics.
- Add automated data-quality checks and repeatable reporting.
- Extend monitoring to account-level transaction sequences and changing activity patterns.

---

## 11. Conclusion

This project demonstrates an end-to-end approach to transaction data preparation, statistical risk screening, SQL-based investigation, reporting, and dashboard development.

It provides a practical foundation for exploring risk indicators and communicating analytical findings while recognizing the limitations of unlabeled data.

---

## 12. Skills Demonstrated

**Programming & Data Analysis:** Python, Pandas, Data Cleaning, Feature Engineering, Exploratory Data Analysis

**Database & Querying:** PostgreSQL, SQL Queries, Aggregation, Account Ranking

**Statistical Analysis:** IQR-Based Outlier Detection, Statistical Risk Scoring, Transaction Monitoring

**Reporting & Visualization:** Microsoft Excel, Pivot Tables, Power BI, DAX, KPI Reporting, Data Visualization

**Business Analysis:** Risk Analysis, Geographic Analysis, Account-Level Monitoring, Data Interpretation
