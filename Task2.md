# 📊 Azure Bill of Materials – Data Integration Architecture

This document outlines the required Azure services and their estimated costs for building a scalable and secure data integration solution. The architecture supports ingesting data from on-prem Oracle, Salesforce, and semi-structured files.

---

## 🔧 Services & Cost Breakdown

### 1. Azure Data Factory (ADF)
- **Purpose**: Orchestrates and automates data ingestion and transformation.
- **Assumptions**:
  - 20 tables from Oracle (on-premises)
  - 120 tables from Salesforce
  - 20 semi-structured files
- **Cost Estimate**:
  - Pipeline runs: $1 per 1,000 runs  
  - Data movement: $0.25 per DIU-hour  
  - **Estimated Monthly Cost**: **~$150**

---

### 2. Azure SQL Database / Azure Synapse Analytics
- **Purpose**: Structured data storage and querying.
- **Assumptions**: 80 GB of incremental data/month
- **Options**:
  - Azure SQL DB (P4): **$1,706.40/month**
  - Azure Synapse (DW1000c): **$4,704/month**
- **Estimated Monthly Cost**: **$2,000 – $5,000**

---

### 3. Azure Blob Storage / Azure Data Lake Storage (ADLS)
- **Purpose**: Store semi-structured files (CSV, JSON, etc.)
- **Assumptions**: 20 files totaling 5 GB/month
- **Cost Estimate**:
  - Hot storage: $0.02/GB  
  - Cool storage: $0.01/GB  
  - **Estimated Monthly Cost**: **$5 – $10**

---

### 4. Azure Logic Apps / Azure Functions
- **Purpose**: Serverless workflows and FTP file automation.
- **Assumptions**: Light volume, automated tasks
- **Cost Estimate**:
  - Logic Apps: $0.000025 per action  
  - Azure Functions: $0.20 per million executions  
  - **Estimated Monthly Cost**: **$10 – $50**

---

### 5. Azure Integration Runtime (Self-hosted)
- **Purpose**: Securely connect to on-premises Oracle databases.
- **Assumptions**:
  - Continuous data extraction
  - Hosted on Azure VM (D4s_v3)
- **Cost Estimate**:
  - VM: $0.192/hour  
  - **Estimated Monthly Cost**: **~$140**

---

### 6. Azure Virtual Network (VNet)
- **Purpose**: Secure networking between Azure and on-premises systems.
- **Assumptions**: Basic VNet for Oracle integration
- **Cost Estimate**:
  - VNet usage: $0.02/hour  
  - **Estimated Monthly Cost**: **~$15**

---

## 💰 Summary Table

| **Service**                    | **Purpose**                             | **Estimated Monthly Cost** |
|-------------------------------|------------------------------------------|-----------------------------|
| Azure Data Factory             | Data ingestion & transformation          | $150                        |
| Azure SQL / Synapse            | Structured data storage & analytics      | $2,000 – $5,000             |
| Blob Storage / ADLS            | Semi-structured file storage             | $5 – $10                    |
| Logic Apps / Azure Functions   | Automation & FTP transfers               | $10 – $50                   |
| Integration Runtime (VM)       | On-prem Oracle integration               | $140                        |
| Virtual Network (VNet)         | Secure on-prem connectivity              | $15                         |
| **Total Estimated Cost**       |                                          | **$2,320 – $5,365**         |
