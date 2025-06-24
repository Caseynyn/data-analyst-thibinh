# data-analyst-thibinh
# Project: **Descriptive Analysis of Delayed Tuition Payments at UCW Finance Department**

The primary goal of this project is to analyze tuition payment data to identify patterns behind delayed payments and help the Finance Department at University Canada West (UCW) enhance cash flow management. This includes evaluating student payment behaviors, understanding delay factors, and proposing improvements in payment processing and financial follow-up systems.

**1. Data Collection and Ingestion**

- Extracted structured datasets related to InvoiceDetails, PaymentRecords, and CustomerProfiles from the UCW Finance data lake.

- Connected AWS S3 buckets (e.g., finance-raw-binh) to ingest raw data.

- Used AWS Glue and Data Catalog to define schema, enabling queries via Athena.

- Ensured data privacy by restricting access to only authorized Finance team roles using IAM and VPC configurations.

- Verified data completeness by validating key fields: InvoiceID, CustomerID, InvoiceDate, DueDate, PaymentDate.

**2. Data Cleaning and Transformation**

- Cleaned data using AWS Glue jobs to remove duplicates, fix formatting issues, and standardize date/time fields.

- Handled missing values (e.g., missing DueDate, PaymentDate) by flagging and imputing where feasible.

- Created curated datasets:

- finance-cur-binh for cleaned payment records

- finance-ETL-binh for transformed datasets with calculated fields (e.g., DaysDelayed = PaymentDate - DueDate)

- Joined tables using common keys (CustomerID, InvoiceID) to create a unified dataset used for further analysis.

**3. Descriptive Statistical Analysis**

- Used Athena queries and Excel to calculate key metrics:

- Average delay in payment across terms

- Number of overdue payments per month

- Common customer profiles with consistent delays

- Categorized delayed payments based on root causes (as identified in the business question matrix).

- Summarized delay trends by:
Time period (e.g., registration peaks); 
Payment method (e.g., digital, wire); 
Student contract terms (credit extension or early/late payment agreement)

- Identified clusters of students who consistently paid late and those who complied with due dates, preparing for segmentation in the next step.

**4. Customer Segmentation**

In this stage, we analyzed the cleaned and joined dataset (finance-ETL-binh) to segment customers based on their payment behaviors using criteria derived from calculated fields like DaysDelayed, TotalAmount, and CreditTerms.

Segmentation Logic:

- Early Payers: Customers who paid invoices ≥ 3 days before the due date.

- On-Time Payers: Customers whose payments matched the due date (± 2 days).

- Late Payers: Customers with average payment delays of more than 3 days.

- Chronic Late Payers: Customers with >50% of invoices delayed beyond 7 days.

Segment Analysis:

- Chronic Late Payers mostly had long credit terms (60–90 days).

- Early Payers often used automated digital payments.

- Late Payers were frequently international accounts with invoice delivery errors or complex billing instructions.

- This segmentation helped target the groups for deeper root cause analysis and policy revision.

**5. Insights and Findings**

Based on our Week 4 analysis and segmentation, the following insights were identified:

Payment Delays Are Systemic: Over 38% of total invoices were paid after the due date, with peak delays occurring near semester starts (January and September).

Top 3 Delay Factors:

- Long payment terms (e.g., 90-day contracts) correlated with a 68% delay rate.

- Invoice delivery issues (missing or erroneous emails) led to a spike in unpaid invoices.

- Lack of follow-up reminders resulted in delays beyond 10 days in 22% of cases.

Chronic Late Payers accounted for over 70% of the total overdue balance, showing a small group significantly affected cash flow.

Digital Payment Users Paid Faster: Those using online banking or auto-pay settled invoices 5–7 days earlier than manual payers.

**6. Recommendations**

To improve cash flow and reduce payment delays, the following actions are recommended:

Revise Credit Terms:

- Shorten standard payment terms from 90 to 45 days for high-risk customers.

- Introduce early-payment incentives and late-payment penalties.

Enhance Invoice Delivery:

- Automate invoice emailing through integration with AWS SES and scheduling services.

- Implement an audit log to track delivery and receipt confirmation.

Improve Follow-Up Processes:

- Schedule automated reminders for approaching and overdue invoices.

- Assign finance team roles in AWS to monitor specific account segments using dashboards.

Monitor Key Segments:

- Track chronic late payers via dashboards (e.g., Power BI, QuickSight).

- Engage these customers with payment restructuring or credit review.

- Leverage Machine Learning (future scope):

- Predict late payments based on customer history, behavior, and payment method.

