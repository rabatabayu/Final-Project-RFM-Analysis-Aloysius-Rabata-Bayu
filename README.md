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

Each customer received an R, F, and M score from **1 to 5**, using a percentile-based ranking approach.

- **Recency:** Lower Recency receives a higher score.
- **Frequency:** Higher Frequency receives a higher score.
- **Monetary:** Higher Monetary receives a higher score.

A customized **rule-based segmentation** approach was then applied to classify customers into eight segments.

The segment definitions are analytical rules adapted for this project rather than universal RFM thresholds.

### 4. Customer Segmentation

| Customer Segment | Customers | Business Priority |
|---|---:|---|
| Champions | 910 | High |
| Loyal Customers | 379 | High |
| Potential Loyalists | 484 | High |
| High-Value At Risk | 142 | Critical |
| At Risk | 614 | Medium |
| Needs Attention | 599 | Medium |
| Recent Low-Frequency | 238 | Medium |
| Hibernating | 968 | Low |
| **Total** | **4,334** | |

Segmentation enables the company to distinguish valuable and active customers from those requiring development, reactivation, or lower-cost engagement strategies.

## Key Business Findings

### 1. Customer Value Is Highly Concentrated

**21% of customers generate 66.01% of total Net Monetary.**

- Champions account for 910 customers, contributing approximately **£5.47 million** in historical Net Monetary.
- Hibernating represents the largest customer segment by count (22.34%) but contributes only **4.18%** of Net Monetary.

**Business Insight:** A relatively small proportion of customers contributes most of the business's historical customer value.

**Recommendation:** Prioritize Champions through VIP rewards, exclusive benefits, and loyalty programs while developing customers with growth potential.

### 2. Champions and Potential Loyalists Support Revenue Growth

Monthly Net Revenue increased from approximately **£923,569 in September 2011 to £1,118,220 in November 2011**, representing growth of **21.1%**.

Customer segment analysis found:

- Champions: approximately **+£194,839**
- Potential Loyalists: approximately **+£116,166**

Other segments experienced declining contributions, partially offsetting these increases.

**Business Insight:** The observed revenue growth was primarily supported by customers classified as Champions and Potential Loyalists.

**Recommendation:** Protect high-value relationships and encourage potential loyal customers to purchase more frequently.

*Note: Monthly contributions use the final RFM segment assignments, not the customers' historical segment membership in each month.*

### 3. Repeat Purchasing Is Strongly Associated with Customer Value

The analysis identified a **65.27% Repeat Purchase Rate**, with 2,829 out of 4,334 customers purchasing more than once.

Spearman correlation results:

| Variable Relationship | Correlation |
|---|---:|
| Frequency vs. Monetary | +0.806 |
| Recency vs. Frequency | -0.564 |
| Recency vs. Monetary | -0.485 |

**Business Insight:** Customers who purchase more frequently and more recently tend to have higher historical purchasing values.

**Recommendation:** Encourage repeat purchases through loyalty initiatives, personalized product recommendations, and targeted incentives.

*Correlation indicates association, not causation.*

### 4. At-Risk Customers Represent Significant Historical Value

Two customer segments require particular attention:

| Segment | Customers | Historical Net Monetary |
|---|---:|---:|
| High-Value At Risk | 142 | £331,348 |
| At Risk | 614 | £515,190 |
| **Combined** | **756** | **£846,538** |

Together, these customers account for approximately **10.22% of total historical Net Monetary**.

**Business Insight:** Previously valuable customers are showing reduced purchasing activity, creating a potential retention risk.

**Recommendation:** Prioritize personalized win-back campaigns for High-Value At Risk customers and targeted reactivation campaigns for At Risk customers.

*Historical Monetary is not a forecast of recoverable revenue.*

## Power BI Dashboard

Two interactive dashboards were developed to translate analytical findings into business insights
