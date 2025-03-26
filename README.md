# Azure Data Engineering Demo

## Project Overview
A demo data engineering project using Azure and SQL Server to showcase Azure skills.
The project addresses a hypothetical need for a business to understand the gender distribution
of its customer base, and how it might influence purchases. The project utilizes a robust pipleline
that will be scheduled to run daily, extract data from on premises SQL Server database, and perform
the necessary transformations to make the data more query friendly.  The transformed data will then
be fed into a custom built report that satisfies the hypothetical requirements. 


![Screenshot 2025-03-26 081944](https://github.com/user-attachments/assets/f5885e2d-b6a0-4ba5-9e91-11b191c6594e)

## Technologies Used
* **SQL Server** for the source data
* **Azure key vault** to securely manage credentials and secrets
* **Azure Data Factory** to retrieve data from SQL 
* **Azure Data Lake** to store the data, and transformations int 3 tiers
  - Bronze for the raw data
  - Silver to transform some data types such as dates to be more report-friendly
  - Gold to change some column names to be more report-friendly 
* **Azure Databricks** with **Python** to perform the transormations
* **Azure Synapse analytics** to load the data
* **PowerBI** to visually show the data to the user

## Setup Instructions
### Prerequisites
* An Azure account with sufficient credits
* Access to an on premises SQL Server

### Step 1: Azure environment setup 
  1. Create Resource Group: Set up a new resource group in Azure.
  2. Provision Services:
    * Create an Azure Data Factory instance.
    * Set up Azure Data Lake Storage with bronze, silver, and gold containers.
    * Set up an Azure Databricks workspace and Synapse Analytics workspace.
    * Configure Azure Key Vault for secret management.
### Step 2: Data Ingestion
   1. Set up SQL Server: Install SQL Server and SQL Server Management Studio (SSMS). Restore the AdventureWorks database.
   2. Ingest Data with ADF: Create pipelines in ADF to copy data from SQL Server to the bronze layer in ADLS.
### Step 3: Data Transformation
   1. Mount Data Lake in Databricks: Configure Databricks to access ADLS.
   2. Transform Data: Use Databricks notebooks to clean and aggregate the data, moving it from bronze to silver and then to gold.
### Step 4: Data Loading and Reporting
   1. Load Data into Synapse: Set up a Synapse SQL pool and load the gold data for analysis.
   2. Create Power BI Dashboard: Connect Power BI to Synapse and create visualizations based on business requirements.
## Step 5: Automation and Monitoring
   1. Schedule Pipelines: Use ADF to schedule the data pipelines to run daily.
   2. Monitor Pipeline Runs: Use the monitoring tools in ADF and Synapse to ensure successful pipeline execution.
### Step 6: Security and Governance
   1. Manage Access: Set up role-based access control (RBAC) using Azure Entra ID (formerly Active Directory).
### Step 7: End-to-End Testing
   1. Trigger and Test Pipelines: Insert new records into the SQL database and verify that the entire pipeline runs successfully, updating the Power BI dashboard.

## Conclusion
This project provides a robust end-to-end solution for understanding customer demographics and their impact on sales. The automated data pipeline ensures that stakeholders always have access to the most current and actionable insights.
