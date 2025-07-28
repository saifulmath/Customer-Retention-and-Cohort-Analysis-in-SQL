📊 Customer Cohort Analysis Using SQL

This project performs cohort analysis on retail transaction data using pure SQL, focusing on understanding customer retention behavior and lifetime value (CLV) over time. The output includes SQL scripts and a PowerPoint presentation for clear storytelling and insights.

🎯 Objective:

To analyze how different customer groups (cohorts) behave over time in terms of:

  1. Retention rate (how many come back)
  2. Lifetime Value (CLV) (how much they spend)

This helps identify patterns of customer loyalty and informs marketing strategies.

📊 Dataset Overview:

 1. Source Table: Online RETAIL ( From Kaggle)
 2. Total Records: 512,909
 3. Records used in final analysis: 375,736

🔍 Data Cleaning & Filtering:

| Criteria                                | Count   |
| --------------------------------------- | ------- |
| Total Transactions                      | 512,909 |
| Suspicious (Quantity ≤ 0)               | 10,126  |
| Canceled Orders (`InvoiceNo LIKE 'C%'`) | 8,836   |
| Missing CustomerID                      | 128,676 |
| Valid Records (Used in Analysis)        | 375,736 |


🧠 SQL Logic (Cohort Analysis)

Step 1: Data Cleaning

WHERE CUSTOMERID IS NOT NULL

  AND CUSTOMERID != ''
  
  AND INVOICENO NOT LIKE 'C%'
  
  AND QUANTITY > 0
  
  AND UNITPRICE > 0

  Step 2: Assign Each Customer a Cohort (First Purchase Month)

  MIN(DATE(FORMATTED_DATE)) OVER (PARTITION BY CUSTOMERID) AS FIRST_TRANSACTION_DATE

  Step 3: Determine CohortIndex (Months since first purchase)

  DATEDIFF(PURCHASE_DATE, FIRST_TRANSACTION_DATE)/30 AS COHORT_MONTH

Step 4: Generate Cohort Tables

   I. Customer Retention Table: Count of unique customers by cohort and month
   
  II. Customer Lifetime Value Table: Sum of revenue by cohort and month


📈 Output Preview is in a PPTX file


📋 Insights & Takeaways

 🔹 Retention drops significantly after Month 1
 
 🔹Certain cohorts (e.g., February, March) show better long-term engagement

 Recommendations:

  🔹 Implement re-engagement campaigns after Month 1
 
  🔹 Design personalized offers for high-value cohorts

📽 Presentation

📎 Customer Cohort Analysis Using SQL.pptx includes:

  🔹Visual breakdown of SQL steps

  🔹Data cleaning summary

  🔹Retention & CLV heatmaps

  🔹Strategic insights and recommendations

🚀 How to Run

  1. Load the RETAIL dataset into a SQL engine ( MySQL).

  2. Execute the cohort_analysis.sql file step-by-step.

  3. Export the results (CSV or Excel).

  4. Use the Excel output to generate visuals or update the included PowerPoint.

🛠 Tools Used

  🔹SQL (Window functions, subquery, CTE, date formatting, filtering, etc.)

  🔹Excel (pivot tables, heatmaps)

  🔹PowerPoint (data storytelling)





  

