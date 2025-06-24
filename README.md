# data-analyst-thibinh
# Project: **Descriptive Analysis of Delayed Tuition Payments at UCW Finance Department**

The primary goal of this project is to analyze tuition payment data to identify patterns behind delayed payments and help the Finance Department at University Canada West (UCW) enhance cash flow management. This includes evaluating student payment behaviors, understanding delay factors, and proposing improvements in payment processing and financial follow-up systems.

**1. Data Profiling**

- Used AWS Glue DataBrew to profile raw datasets stored in an S3 bucket.

- Evaluated nulls, outliers, and type mismatches.

- Found inconsistencies in Payment_Status and missing values in Payment_Method.

**2. Data Cleaning & Cataloging**

Cleaned dataset by:

- Removing null rows in critical fields.

- Standardizing Payment_Method entries (e.g., "cc" → "Credit Card").

- Converting string date fields to datetime.

Designed and documented cleaning steps using **AWS DataBrew** jobs.

Registered cleaned dataset into **AWS Glue Data Catalog**.

**3. Descriptive Statistical Analysis**

Performed exploratory analysis using Athena + Google Collab:

- Total monthly payments and average transaction value.

- Distribution of payment methods.

- Payment completion rate by semester and location.

Visualizations:

*Monthly Delayed Payments Trend*
![image](https://github.com/user-attachments/assets/5552c1e5-78fb-49b0-adc1-5e3a004f3629)

*Customer Segmentation*

<img width="789" alt="Screenshot 2025-06-23 at 10 21 44 PM" src="https://github.com/user-attachments/assets/d60410e4-0609-4a5f-b30b-4061290d6f96" />

*Delay Reasons*

<img width="689" alt="Screenshot 2025-06-23 at 10 24 46 PM" src="https://github.com/user-attachments/assets/eaa707e5-c58e-4258-9061-a65106d0170a" />

*Top 10 Delinquent Customers*

<img width="793" alt="Screenshot 2025-06-23 at 10 28 08 PM" src="https://github.com/user-attachments/assets/3246c063-6b4d-4193-9fad-c011adb7928f" />


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

***Tools and Technologies***

- AWS S3 – data storage

- AWS Glue DataBrew – profiling & cleaning

- AWS Glue Catalog – metadata registry

- AWS Athena – SQL-based querying

- Google Collab – Data visualization

- Excel – initial inspection and schema design & dashboard

***Estimated AWS Cost***

Based on the usage of DataBrew and Athena:

- AWS Glue (DataBrew jobs + profiling): ~$3.41/month

- Athena queries (per GB scanned): Est. $1–$2 for demo usage

***Deliverables***

- Cleaned finance dataset in .csv format

- Weekly design and progress reports

***AWS Deployment and Service Models***

Traditional Computing Model vs Cloud Computing Model

<img width="656" alt="Screenshot 2025-06-23 at 8 50 13 PM" src="https://github.com/user-attachments/assets/a210af7d-43a6-4a76-ab2b-c12299700800" />
<img width="448" alt="Screenshot 2025-06-23 at 9 44 24 PM" src="https://github.com/user-attachments/assets/5ec18030-cf11-4460-8d3e-cb2a5f870c6a" />

Cloud Deployment Models
<img width="864" alt="Screenshot 2025-06-23 at 9 48 48 PM" src="https://github.com/user-attachments/assets/f6ec07ec-b030-4e32-ab63-398030d37eb4" />
<img width="964" alt="Screenshot 2025-06-23 at 9 50 53 PM" src="https://github.com/user-attachments/assets/547f6569-b162-4e80-a5dc-48916a8df7b7" />

Cloud Service Models

<img width="804" alt="Screenshot 2025-06-23 at 9 52 48 PM" src="https://github.com/user-attachments/assets/e5679ea6-7bb4-44f9-9fc7-59f2ba95f8ee" />
<img width="986" alt="Screenshot 2025-06-23 at 9 53 13 PM" src="https://github.com/user-attachments/assets/2c43a5fe-6a21-4c44-8b08-3837f5f98b9f" />

Module 1 Knowledge Check

<img width="327" alt="Screenshot 2025-06-23 at 9 58 31 PM" src="https://github.com/user-attachments/assets/31d1c9d0-1e55-407e-be3d-aec98223f80a" />



***AWS Cost Analysis***

Total Cost Of Ownership - Delaware North

<img width="203" alt="Screenshot 2025-06-23 at 10 02 44 PM" src="https://github.com/user-attachments/assets/23d67462-30dc-4624-86fe-4fa2b652b9f7" />

AWS Pricing Calculator

<img width="957" alt="Screenshot 2025-06-23 at 9 56 22 PM" src="https://github.com/user-attachments/assets/a8c16022-e4d9-4efa-b9a0-252a19c3b570" />

Support Plan

<img width="573" alt="Screenshot 2025-06-23 at 10 00 11 PM" src="https://github.com/user-attachments/assets/7cc84837-e1f7-476c-b144-0f6c46181949" />

Module 2 Knowledge Check

<img width="555" alt="Screenshot 2025-06-23 at 10 00 48 PM" src="https://github.com/user-attachments/assets/16d4ff7b-8d4e-4f07-b52f-b6496b2b4364" />

***AWS Global infrastructure***

AWS Global Infrastruture

<img width="701" alt="Screenshot 2025-06-23 at 10 04 26 PM" src="https://github.com/user-attachments/assets/5cda5956-e6ab-4b08-a1f6-126bbf7473a2" />
<img width="470" alt="Screenshot 2025-06-23 at 10 04 47 PM" src="https://github.com/user-attachments/assets/5b74af2f-8104-4b56-85af-98a10c4b6d21" />

Module 3 Knowledge Check

<img width="381" alt="Screenshot 2025-06-23 at 10 05 21 PM" src="https://github.com/user-attachments/assets/026b3366-8df7-4fd4-ad74-01758c6d75a4" />

***AWS IAM***

IAM practrice: Lab 1

<img width="256" alt="Screenshot 2025-06-23 at 10 06 35 PM" src="https://github.com/user-attachments/assets/bcd33b96-a3b3-40c4-9a50-2bb91fc17046" />

Module 4 Knowledge Check

<img width="441" alt="Screenshot 2025-06-23 at 10 07 01 PM" src="https://github.com/user-attachments/assets/12ae843b-375a-44ac-97e1-e78873ceef66" />

***AWS VPC***

Build your VPC: Lab 2

<img width="319" alt="Screenshot 2025-06-23 at 10 08 26 PM" src="https://github.com/user-attachments/assets/de301f41-72e7-4a6e-9ec2-fe9cbf003d4f" />

Module 5 Knowledge Check

<img width="450" alt="Screenshot 2025-06-23 at 10 08 53 PM" src="https://github.com/user-attachments/assets/a79cea97-229d-4dfd-bb00-9ea3a7d60bd5" />

***AWS Lambda***

Create an AWS Lambda function

<img width="431" alt="Screenshot 2025-06-23 at 10 09 39 PM" src="https://github.com/user-attachments/assets/fe395a21-9530-4c1b-864b-21693e9cc810" />

Module 6 Knowledge Check

<img width="493" alt="Screenshot 2025-06-23 at 10 09 59 PM" src="https://github.com/user-attachments/assets/a95fd1fb-9c09-496e-8eb9-008cbaf5825b" />

***AWS EBS***

Working with Amazon EBS: Lab 4

<img width="462" alt="Screenshot 2025-06-23 at 10 11 10 PM" src="https://github.com/user-attachments/assets/10917e51-5be9-4536-afad-8bf5d235bc2b" />

Module 7 Knowledge Check

<img width="528" alt="Screenshot 2025-06-23 at 10 11 32 PM" src="https://github.com/user-attachments/assets/82b3ae83-6076-4471-a5ff-d0c773586e9d" />
























