# Bank-Loan-Performance-Dashboard-with-Tableau-SQL
Developed a high-level Tableau dashboard with SQL validation to analyze loan trends, funding, and borrower behavior, optimizing lending strategies and  financial oversight.
### Project Overview

The Bank Loan Report project aims to create a comprehensive dashboard that provides insights into key metrics related to loan applications, loan amounts, borrower profiles, and loan repayment statuses. By utilizing SQL queries to extract, process, and verify data, the report will empower stakeholders to track performance, assess portfolio health, and make informed decisions to optimize lending strategies.

### Problem Statement

To monitor and evaluate the bank’s lending operations effectively, it is crucial to generate a detailed report. This project focuses on building a dynamic dashboard that offers insights into total loan applications, funding trends, borrower behavior, and the performance of the bank’s loan portfolio. Using SQL queries, the project will verify data accuracy and ensure that all key metrics are correctly calculated for decision-making.

**Research Question:**  
How can SQL-powered dashboards provide actionable insights into loan performance, including trends, funding, repayment, and borrower characteristics, to optimize lending strategies?

### Tools and Libraries Used

- **Data Retrieval and Verification**: SQL (MySQL/PostgreSQL)
- **Data Manipulation and Analysis**: Pandas, NumPy
- **Data Visualization**: Matplotlib, Seaborn, Plotly
- **Dashboard**: Tableau or Power BI (for visualization)
- **Business Intelligence and Reporting**: SQL-based reports and queries

### Dataset Description

The dataset contains loan application and repayment data, including:

- **Loan ID**: Unique identifier for each loan
- **Address State**: The state where the borrower resides
- **Application Type**: Type of application (e.g., individual)
- **Employee Length**: Duration of employment of the borrower
- **Grade & Sub-Grade**: Risk classifications for the loan
- **Home Ownership**: The borrower’s housing status
- **Issue Date, Last Payment Date, Next Payment Date**: Key loan timing details
- **Loan Status**: Indicates if the loan is paid off, current, or charged off
- **Loan Amount**: The total amount requested for the loan
- **Interest Rate, DTI**: Financial parameters affecting the loan agreement
- **Installment, Total Payment**: Loan repayment schedule and amounts

### Steps Undertaken

#### 1. Data Cleaning and Preparation
- **SQL Verification**: Created SQL queries to ensure data integrity for each loan record (e.g., checking for missing values, mismatched dates).
- **Column Conversion**: Ensured all monetary, date, and numeric columns were correctly formatted.
- **Data Aggregation**: Used SQL queries to aggregate monthly, region-based, and loan-status-specific metrics for analysis.

#### 2. Key Performance Indicators (KPIs) Analysis
SQL queries were used to calculate and verify critical KPIs for loan performance:

- **Total Loan Applications**: `SELECT COUNT(id) AS Total_Applications FROM bank_loan_data`
- **Total Funded Amount**: `SELECT SUM(loan_amount) AS Total_Funded_Amount FROM bank_loan_data`
- **Total Amount Received**: `SELECT SUM(total_payment) AS Total_Amount_Collected FROM bank_loan_data`
- **Average Interest Rate**: `SELECT AVG(int_rate) * 100 AS Avg_Int_Rate FROM bank_loan_data`
- **Average DTI**: `SELECT AVG(dti) AS Avg_DTI FROM bank_loan_data`

#### 3. Good Loan vs. Bad Loan KPIs

SQL was used to separate and assess the quality of loans based on status:

- **Good Loan KPIs** (Loans marked as "Fully Paid" or "Current")
  - **Good Loan Application Percentage**: `SELECT (COUNT(id) / (SELECT COUNT(id) FROM bank_loan_data)) * 100 AS Good_Loan_Percentage FROM bank_loan_data WHERE loan_status IN ('Fully Paid', 'Current')`
  - **Good Loan Funded Amount**: `SELECT SUM(loan_amount) AS Good_Loan_Funded_Amount FROM bank_loan_data WHERE loan_status IN ('Fully Paid', 'Current')`

- **Bad Loan KPIs** (Loans marked as "Charged Off")
  - **Bad Loan Application Percentage**: `SELECT (COUNT(id) / (SELECT COUNT(id) FROM bank_loan_data)) * 100 AS Bad_Loan_Percentage FROM bank_loan_data WHERE loan_status = 'Charged Off'`
  - **Bad Loan Funded Amount**: `SELECT SUM(loan_amount) AS Bad_Loan_Funded_Amount FROM bank_loan_data WHERE loan_status = 'Charged Off'`

#### 4. Visual Representation via Dashboards

##### **Dashboard 1: Summary**
Using the SQL queries for aggregating key metrics, a dashboard was built to track overall loan performance and regional trends.

- **Loan Status Grid View**: SQL queries categorized by loan status, showing the total loan applications, funded amounts, and repayments for each status.
- **Monthly Trends by Issue Date**: Line charts created by aggregating monthly data using SQL to track applications, funds, and received amounts over time.
- **Regional Analysis by State**: Filled maps to represent loan data by geographic regions, sourced from SQL query results.

##### **Dashboard 2: Loan Term and Purpose Breakdown**
- **Loan Term Analysis**: SQL queries grouped loan data by term and analyzed funding distributions.
- **Loan Purpose Breakdown**: SQL aggregated data by loan purpose to understand borrower needs and loan trends.

##### **Dashboard 3: Loan Details**
- A comprehensive details dashboard that provided in-depth loan status information, including issue dates, payment history, and loan status updates.
  
#### 5. Temporal Analysis
- **Trend Analysis**: Used SQL to aggregate loan applications and repayments month over month to identify patterns, such as peak loan application months and fluctuations in funding amounts.

#### 6. Cost and Profitability Analysis
- **Profitability**: SQL queries were used to track how the total amount collected from loan payments compares to the funded amount, assessing loan portfolio profitability.

#### 7. Cointegration and Data Relationships
- **Correlation Testing**: Used SQL and statistical methods to analyze the relationship between loan characteristics (e.g., interest rates, DTI) and loan status. This helped identify patterns in loan repayment behavior and borrower stability.

### Key Findings

- **Loan Application Volume**: The total number of loan applications steadily increased over the year, with noticeable peaks during certain months (e.g., December).
- **Regional Differences**: Significant regional disparities in loan applications and funded amounts, suggesting targeted marketing opportunities.
- **Good Loans vs. Bad Loans**: A significant proportion of loans were classified as "Good Loans," indicating a healthy lending portfolio.
- **Interest Rate Trends**: A gradual decline in average interest rates over the year, offering insights into changing lending strategies.
- **Repayment Patterns**: Strong correlations were observed between borrower income and loan repayment behaviors.

### Business Impact

This analysis will provide banks with the tools to:
- **Optimize Lending Strategies**: Allocate resources to regions and periods with higher application volumes and better repayment performance.
- **Risk Assessment**: Identify trends in good vs. bad loans, enabling better credit risk management.
- **Decision Making**: Use SQL-powered insights to make more data-driven decisions regarding loan offerings, terms, and regional outreach.
  
### Conclusion

By leveraging SQL queries to extract, clean, and analyze data, this project provides a robust framework for tracking, evaluating, and optimizing lending operations. The insights gathered through the dashboards and KPIs will enable banks to improve loan portfolio management, minimize risk, and maximize profitability.
