# data-analyst-thibinh
# Project 1: **Descriptive Analysis of Delayed Tuition Payments at UCW Finance Department**

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

[Estimated Cost_AWS Glue.pdf](https://github.com/user-attachments/files/20877199/Estimated.Cost_AWS.Glue.pdf)

[Estimated Cost_S3.pdf](https://github.com/user-attachments/files/20877201/Estimated.Cost_S3.pdf)

- Athena queries (per GB scanned): Est. $1–$2 for demo usage
  
[Estimated Cost_Athena.pdf](https://github.com/user-attachments/files/20877176/Estimated.Cost_Athena.pdf)


***Deliverables***

- Cleaned finance dataset in .csv format

- Weekly design and progress reports

[Finance-DAP-Progress-Report-Thi Binh Nguyen.pdf](https://github.com/user-attachments/files/20877247/Finance-DAP-Progress-Report-Thi.Binh.Nguyen.pdf)

[Finance-DAP-Progress-Report-Binh.pdf](https://github.com/user-attachments/files/20877260/Finance-DAP-Progress-Report-Binh.pdf)


---
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

**Status:** ✅ Completed | Score: 100/100 (100%)

**Topic:** Introduction to Cloud Computing and AWS Core Services

🔍 Module Objectives:

- Define different types of cloud computing models (IaaS, PaaS, SaaS)
- Describe six key advantages of cloud computing
- Recognize AWS service categories and core offerings
- Review the AWS Cloud Adoption Framework

<img width="327" alt="Screenshot 2025-06-23 at 9 58 31 PM" src="https://github.com/user-attachments/assets/31d1c9d0-1e55-407e-be3d-aec98223f80a" />

---

***AWS Cost Analysis***

Total Cost Of Ownership - Delaware North

<img width="203" alt="Screenshot 2025-06-23 at 10 02 44 PM" src="https://github.com/user-attachments/assets/23d67462-30dc-4624-86fe-4fa2b652b9f7" />

AWS Pricing Calculator

<img width="957" alt="Screenshot 2025-06-23 at 9 56 22 PM" src="https://github.com/user-attachments/assets/a8c16022-e4d9-4efa-b9a0-252a19c3b570" />

Support Plan

<img width="573" alt="Screenshot 2025-06-23 at 10 00 11 PM" src="https://github.com/user-attachments/assets/7cc84837-e1f7-476c-b144-0f6c46181949" />


Module 2 Knowledge Check

**Status:** ✅ Completed | Score: 90/100 (90%)

**Topic:** AWS Pricing Models, Billing Tools, and Support Plans

🔍 Module Objectives:

- Explore the fundamental principles of AWS pricing (pay-as-you-go, save-when-you-reserve, volume-based discounts)
- Review TCO (Total Cost of Ownership) concepts and comparison with on-premise costs
- Learn how to generate cost estimates using the AWS Pricing Calculator
- Understand how to monitor and manage billing through the AWS Billing Dashboard
- Review AWS Technical Support Plans, including developer, business, and enterprise tiers

<img width="555" alt="Screenshot 2025-06-23 at 10 00 48 PM" src="https://github.com/user-attachments/assets/16d4ff7b-8d4e-4f07-b52f-b6496b2b4364" />

---
***AWS Global infrastructure***

AWS Global Infrastruture

<img width="701" alt="Screenshot 2025-06-23 at 10 04 26 PM" src="https://github.com/user-attachments/assets/5cda5956-e6ab-4b08-a1f6-126bbf7473a2" />
<img width="470" alt="Screenshot 2025-06-23 at 10 04 47 PM" src="https://github.com/user-attachments/assets/5b74af2f-8104-4b56-85af-98a10c4b6d21" />


Module 3 Knowledge Check

**Status:** ✅ Completed | **Score:** 100/100 (100%)  

**Topic:** AWS Global Infrastructure and Service Categories

🔍 Module Objectives:

- Identify the difference between AWS Regions, Availability Zones, and edge locations
- Identify AWS services and categorize them appropriately  

<img width="381" alt="Screenshot 2025-06-23 at 10 05 21 PM" src="https://github.com/user-attachments/assets/026b3366-8df7-4fd4-ad74-01758c6d75a4" />

---
***AWS IAM***

IAM practrice: Lab 1

**Topic:** Managing Identity and Access in AWS using IAM

**Lab Objectives:**

This lab provides hands-on experience with AWS Identity and Access Management (IAM) to help you understand how AWS manages users, groups, and permissions securely and effectively. By completing this lab, you will:

- Explore **pre-created IAM users and groups** within the AWS environment.
- Understand how **IAM policies** (managed and inline) control access to AWS resources.
- Simulate a **real-world scenario** by assigning users to appropriate IAM groups based on job roles and required permissions.
- Locate and utilize the **IAM user sign-in URL** to test access capabilities.
- Observe how **permission boundaries affect user actions** on AWS services like EC2 and S3.

**Key Skills Practiced:**

- Navigating the **IAM Console** to inspect users, groups, policies, and permissions.
- Adding users to IAM groups with **predefined permission policies** (AmazonEC2ReadOnlyAccess, AmazonS3ReadOnlyAccess).
- Differentiating between **Managed Policies** and **Inline Policies**.
- Logging in as IAM users to **validate access rights** and demonstrate the effect of attached policies.
- Understanding **least privilege access** by testing what users can and cannot do based on their group membership.

**Real-World Scenario Practiced:**

You configured IAM access for three fictional employees:
| User    | Group         | Permissions                                 |
|---------|---------------|---------------------------------------------|
| user-1  | S3-Support     | Read-only access to Amazon S3               |
| user-2  | EC2-Support    | Read-only access to Amazon EC2              |
| user-3  | EC2-Admin      | View, start, and stop EC2 instances         |

Each user's access level was verified by signing in via a unique IAM URL and attempting permitted and restricted actions within the AWS Console.

✅ **Outcome:**

This lab solidified foundational knowledge of AWS IAM by demonstrating how centralized identity and access control works in practice. It reinforced the importance of **policy-based access control**, and how IAM enables secure and scalable AWS operations.

<img width="256" alt="Screenshot 2025-06-23 at 10 06 35 PM" src="https://github.com/user-attachments/assets/bcd33b96-a3b3-40c4-9a50-2bb91fc17046" />


Module 4 Knowledge Check

**Status:** ✅ Completed | Score: 100/100 (100%)  

**Topic:** AWS Security and IAM

🔍 Module Objectives:

- Recognize the shared responsibility model between AWS and the customer
- Identify the responsibilities of both the customer and AWS
- Understand IAM (Identity and Access Management) concepts including users, groups, and roles
- Describe types of IAM security credentials
- Outline steps to secure a new AWS account
- Explore access control using IAM users and groups
- Learn how to protect data stored in AWS
- Recognize AWS compliance and governance programs

<img width="441" alt="Screenshot 2025-06-23 at 10 07 01 PM" src="https://github.com/user-attachments/assets/12ae843b-375a-44ac-97e1-e78873ceef66" />

---
***AWS VPC***

Build your VPC: Lab 2

**Topic:** Custom VPC Networking & EC2 Web Server Deployment

**Lab Objectives:**
- Create a custom Amazon VPC with both public and private subnets across multiple Availability Zones
- Configure route tables, NAT Gateway, and Internet Gateway for controlled internet access
- Create and apply VPC Security Groups for controlled traffic flow (HTTP access)
- Launch and configure an EC2 instance in the public subnet with:
- Amazon Linux 2023 AMI
- Apache HTTP server and PHP installed
- A sample PHP web app deployed via user data script
- Access the deployed website through the instance’s public DNS to validate successful setup

Final Architecture Highlights:
- 1 VPC spanning 2 Availability Zones
- 4 subnets (2 public, 2 private)
- 2 route tables (for public and private routing)
- 1 NAT Gateway for internet access from private subnet
- 1 Internet Gateway for direct public access
- 1 EC2 instance running a web server with a deployed application
- 1 security group allowing HTTP traffic from the internet

<img width="319" alt="Screenshot 2025-06-23 at 10 08 26 PM" src="https://github.com/user-attachments/assets/de301f41-72e7-4a6e-9ec2-fe9cbf003d4f" />


Module 5 Knowledge Check

Status: ✅ Completed | Score: 100/100 (100%)

Topic: Cloud Networking and Content Delivery

🔍 Module Objectives:
- Recognize the basics of networking in the cloud
- Describe virtual networking using Amazon VPC (Virtual Private Cloud)
- Label and interpret a basic network diagram
- Design a basic VPC architecture
- Identify and sequence the steps to build a VPC
- Define security groups and their role in controlling access
- Create a custom VPC and integrate additional networking components
- Understand the fundamentals of Amazon Route 53 for DNS management
- Recognize the use cases and benefits of Amazon CloudFront for content delivery

<img width="450" alt="Screenshot 2025-06-23 at 10 08 53 PM" src="https://github.com/user-attachments/assets/a79cea97-229d-4dfd-bb00-9ea3a7d60bd5" />

---
***AWS Lambda***

Create an AWS Lambda function

**Topic:** Automating EC2 Stop Actions Using AWS Lambda and Amazon EventBridge

🔍 Lab Objectives:
- Create and configure an AWS Lambda function using Python runtim
- Assign a pre-existing IAM role to the Lambda function to allow EC2 control
- Configure a scheduled Amazon EventBridge rule to trigger the Lambda function every minute
- Write and deploy Lambda code to stop a specific Amazon EC2 instance
- Use dynamic values such as Region and EC2 Instance ID in function configuration
- Monitor Lambda execution results using the Monitoring dashboard
- Verify the automation works by observing EC2 instance state changes
- Explore the idea of serverless automation as a cron job alternative in AWS

<img width="431" alt="Screenshot 2025-06-23 at 10 09 39 PM" src="https://github.com/user-attachments/assets/fe395a21-9530-4c1b-864b-21693e9cc810" />


Module 6 Knowledge Check

Status: ✅ Completed | Score: 100/100 (100%)

Topic: AWS Compute Services and EC2 Fundamentals

🔍 Module Objectives:
- Provide an overview of different AWS compute services in the cloud
- Demonstrate why to use Amazon Elastic Compute Cloud (Amazon EC2)
- Identify the functionality in the Amazon EC2 console
- Perform basic functions in Amazon EC2 to build a virtual computing environment
- Identify Amazon EC2 cost optimization elements
- Demonstrate when to use AWS Elastic Beanstalk
- Demonstrate when to use AWS Lambda
- Identify how to run containerized applications in a cluster of managed servers

<img width="493" alt="Screenshot 2025-06-23 at 10 09 59 PM" src="https://github.com/user-attachments/assets/a95fd1fb-9c09-496e-8eb9-008cbaf5825b" />

---
***AWS EBS***

Working with Amazon EBS: Lab 4

**Topic:** Amazon Elastic Block Store (EBS) – Volumes, Snapshots, and Restore Operations

**Lab Objectives:**
By the end of this hands-on lab, I was able to:
- Create an Amazon EBS volume and configure tags for easy identification
- Attach and mount an EBS volume to an Amazon EC2 instance using the AWS Console and EC2 Instance Connect
- Format the volume with an ext3 filesystem and ensure persistent mounting using the /etc/fstab file
- Verify volume usage by writing, viewing, and deleting data from the mounted directory
- Create a snapshot of the volume to enable data backup with high durability in Amazon S3
- Restore data by creating a new volume from the snapshot and mounting it to the instance to retrieve original data

**Key Concepts Practiced:**
- Amazon EBS lifecycle: create → attach → use → snapshot → restore
- Use of mkfs, mount, df, ls, and cat commands in EC2 Instance Connect
- Working with persistent and replicated block-level storage
- Managing Linux file systems and automating mount operations with fstab
- Snapshot-based disaster recovery and cross-volume data access

<img width="462" alt="Screenshot 2025-06-23 at 10 11 10 PM" src="https://github.com/user-attachments/assets/10917e51-5be9-4536-afad-8bf5d235bc2b" />


Module 7 Knowledge Check

Status: ✅ Completed | Score: 100/100 (100%)

Topic: AWS Storage Solutions – S3, EBS, EFS, and Glacier

🔍 Module Objectives:
- Identify the different types of storage offered in AWS
- Explain Amazon S3 and its core functionalities
- Identify how Amazon S3 can be used in cloud storage solutions
- Explain Amazon Elastic Block Store (EBS) and its capabilities
- Perform functions in Amazon EBS to support EC2-based architecture
- Explain Amazon Elastic File System (EFS) and recognize its use case
- Explain Amazon S3 Glacier for archival storage
- Differentiate among Amazon S3, EBS, EFS, and S3 Glacier in terms of performance, durability, and cost efficiency

<img width="528" alt="Screenshot 2025-06-23 at 10 11 32 PM" src="https://github.com/user-attachments/assets/82b3ae83-6076-4471-a5ff-d0c773586e9d" />


# Project 2 (Group project): **AWS Data Analytic Platform for The City of Vancouver**

The City of Vancouver processes a variety of services and operations which is a significant source of data. To enhance decision-making processes that are founded on data, as well as for the sake of the City's transparency, it is critical for the City to have a defined framework. This framework is a Data Analytic Platform (DAP) which allows the City to manage and analyze their data, helping departments to understand trends, fill gaps, and optimally allocate resources.

[BUSI653_04_Group 2_Project Phase 1.pdf](https://github.com/user-attachments/files/20876626/BUSI653_04_Group.2_Project.Phase.1.pdf)


[BUSI653_04_Group 1_Project Phase 2.pdf](https://github.com/user-attachments/files/20876643/BUSI653_04_Group.1_Project.Phase.2.pdf)

The project phase 1 and 2 have achieved the primary goal of using essential AWS services to create a functioning DAP which follows the standard 5-stage data pipeline. We demonstrated practice fully in naming, encryption and separation of storage zones. However, to go deeper into the project under Module 9 recommendations, we need to improve automation, monitoring, performance optimization and cost control strategies. If these improvements are taken, the DAP will be more robust, scalable and ready for enterprises























