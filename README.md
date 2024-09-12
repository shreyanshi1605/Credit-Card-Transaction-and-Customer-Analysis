# Credit-Card-Transaction-and-Customer-Analysis

🚀 𝑷𝒓𝒐𝒋𝒆𝒄𝒕 𝑯𝒊𝒈𝒉𝒍𝒊𝒈𝒉𝒕: 𝑪𝒐𝒎𝒑𝒓𝒆𝒉𝒆𝒏𝒔𝒊𝒗𝒆 𝑪𝒓𝒆𝒅𝒊𝒕 𝑪𝒂𝒓𝒅 𝑻𝒓𝒂𝒏𝒔𝒂𝒄𝒕𝒊𝒐𝒏 & 𝑪𝒖𝒔𝒕𝒐𝒎𝒆𝒓 𝑨𝒏𝒂𝒍𝒚𝒔𝒊𝒔 💳

I'm excited to share my latest project, where I performed a deep dive into credit card transactions and customer data to uncover valuable insights into spending behaviors, revenue generation, and customer segmentation. The analysis aimed to inform strategic decisions for optimizing credit card offerings and enhancing customer satisfaction.

𝐊𝐞𝐲 𝐓𝐚𝐤𝐞𝐚𝐰𝐚𝐲𝐬:

𝑻𝒓𝒂𝒏𝒔𝒂𝒄𝒕𝒊𝒐𝒏 𝑨𝒏𝒂𝒍𝒚𝒔𝒊𝒔:

1. Revenue Trends: The analysis identified that quarterly revenue peaks in Q4 across all card categories, with Blue cardholders contributing the highest revenue of $46.1M. 
2. Expenditure Breakdown: Categories such as bills, entertainment, and fuel emerged as the top revenue generators, each contributing over $8M.
3. State-wise Performance: States like New York ($7.1M) and California ($6.5M) led in revenue generation.

𝑪𝒖𝒔𝒕𝒐𝒎𝒆𝒓 𝑨𝒏𝒂𝒍𝒚𝒔𝒊𝒔:

1. Income Group Segmentation: High-income groups contributed $22M, while middle-income groups added $18M.
2. Demographic Insights: Business professionals and white-collar workers were the highest revenue contributors, generating $17.3M and $10.1M, respectively.
3. Marital and Dependent Influence: Married individuals contributed $15M in revenue, and families with two dependents showed significant spending patterns.
4. Educational Impact: Graduates contributed the most to revenue at $12M, indicating that higher education correlates with higher spending.
   
🛠️ Project Workflow:

1. Import Data from SQL Database: Extracted large volumes of transaction and customer data from the SQL database, ensuring data integrity and accuracy for subsequent analysis.
2. Data Processing & DAX Query: Cleaned and transformed the dataset, handling missing values and performing data aggregation. Utilized DAX (Data Analysis Expressions) queries to calculate metrics such as revenue, transaction counts, and customer segments.
3. Design Dashboard & Insights: Designed an interactive Power BI dashboard to visualize key trends, revenue streams, and customer segments. Derived actionable insights from charts and graphs, enabling strategic decision-making for credit card offerings and customer engagement.

### DAX Queries
```
AgeGroup = SWITCH(
TRUE(),
'public cust_detail'[customer_age] < 30, "20-30",
'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
'public cust_detail'[customer_age] >= 60, "60+",
"unknown"
)
```
```
IncomeGroup = SWITCH(
TRUE(),
'public cust_detail'[income] < 35000, "Low",
'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
'public cust_detail'[income] >= 70000, "High",
"unknown"
)
```
```
week_num2 = WEEKNUM('public cc_detail'[week_start_date])
Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]
Current_week_Reveneue = CALCULATE(
SUM('public cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])))
Previous_week_Reveneue = CALCULATE(
SUM('public cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))
```
Screenshots:

### Credit Card Transaction Report
![image](https://github.com/user-attachments/assets/dbbc4112-c145-4f30-adcc-4048cd3a0740)

### Credit Card Customer Report
![image](https://github.com/user-attachments/assets/d08e407a-65e9-494c-9741-0bb972900800)
