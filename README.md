# Online Retail Customer Segmentation Using RFM Analysis

### End-to-End Data Analytics Project | Python • Power BI • Customer Analytics

## Project Overview

This project analyzes transactional data from an online retail business to understand customer purchasing behavior, identify high-value customers, and develop targeted customer retention strategies.

Using **Recency, Frequency, and Monetary (RFM) Analysis**, customers are classified into eight behavioral segments based on their purchasing activity and contribution to business revenue.

The project combines data cleaning, exploratory data analysis, customer segmentation, interactive Power BI dashboards, and actionable business recommendations.

## Business Problem

Not all customers contribute equally to business revenue. Without a clear understanding of purchasing behavior, companies risk allocating marketing resources inefficiently, overlooking valuable customers, and missing opportunities to improve retention.

This project addresses three key business questions:

1. **Revenue Growth:** How can the company maximize revenue from its existing customer base?
2. **Customer Retention:** How can the company encourage repeat purchases and reduce the risk of customer inactivity?
3. **Marketing Prioritization:** Which customers should be prioritized for loyalty, development, and reactivation campaigns?

## Dataset Overview

**Source:** [UCI Machine Learning Repository — Online Retail](https://archive.ics.uci.edu/dataset/352/online+retail)

The dataset contains transaction records from a UK-based online retail business covering December 2010 to December 2011.

| Dataset Information | Value |
|---|---|
| Original Records | 541,909 |
| Original Features | 8 |
| Final RFM Customers | 4,334 |
| Customer Segments | 8 |
| Total Net Monetary | £8,284,890.08 |
| Analysis Tools | Python, Jupyter Notebook, Power BI |

**Original Features:** InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, and Country.

## Tools & Technologies

| Tool | Purpose |
|---|---|
| Python | Data cleaning, feature engineering, EDA, and RFM analysis |
| Pandas & NumPy | Data manipulation and calculations |
| Matplotlib & Seaborn | Data visualization |
| SciPy | Statistical analysis |
| Power BI | Interactive dashboards and business intelligence |
| DAX | KPI calculations and analytical measures |
| Jupyter Notebook | End-to-end analysis documentation |

## Analytical Workflow

### 1. Data Understanding & Cleaning

Data quality was assessed before performing customer segmentation.

Key processes included:

- **Data Inconsistency:** Standardized text formatting by removing unnecessary whitespace and normalizing capitalization.
- **Missing Values:** Identified 135,080 missing CustomerID values (24.93%). Transactions without CustomerID were excluded from customer-level RFM analysis while the original transactional dataset was preserved.
- **Duplicate Assessment:** Identified 5,268 additional duplicate rows (0.97%). Exact duplicates were retained because identical transaction lines may represent valid repeated item entries, and no unique invoice-line identifier or system audit trail was available to verify them.
- **Data Type Handling:** Converted InvoiceDate into datetime format and standardized identifier and numerical data types.
- **Outlier Detection:** Used the Interquartile Range (IQR) method and boxplots. Potentially valid extreme transaction values were retained to preserve high-value purchasing behavior.
- **Transaction Validation:** Evaluated purchases, returns, and non-product adjustments to support the calculation and reconciliation of Net Monetary.

### 2. Exploratory Data Analysis (EDA)

EDA focused on understanding transactional characteristics before introducing customer segmentation.

**Distribution Analysis**

Histograms and KDE plots were used to examine Quantity and UnitPrice distributions, including skewness and extreme transaction values.

**Correlation Analysis**

Pearson and Spearman correlation analyses were used to investigate relationships between numerical transaction variables.

These analyses provided an understanding of transaction-level purchasing patterns. However, they could not independently identify which customers were most valuable, frequently active, or at risk of becoming inactive.

This analytical gap motivated the use of RFM Customer Segmentation.

### 3. RFM Feature Engineering

Customer purchasing behavior was summarized using three metrics.

| Metric | Definition | Business Interpretation |
|---|---|---|
| Recency | Days since the customer's most recent purchase | Lower values indicate more recent activity |
| Frequency | Number of purchasing transactions | Higher values indicate more frequent purchasing |
| Monetary | Total net purchasing value | Higher values indicate greater historical customer value |

Each customer received an R, F, and
