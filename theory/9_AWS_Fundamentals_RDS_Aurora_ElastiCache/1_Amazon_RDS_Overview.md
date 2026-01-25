# Amazon RDS Overview (Relational Database Service)

## 1. What is Amazon RDS?
Amazon RDS is a **managed database service** that makes it easy to set up, operate, and scale a relational database in the cloud.
- It automates time-consuming administration tasks like hardware provisioning, database setup, patching, and backups.
- **Important:** You **cannot** SSH into the underlying RDS instance (it is fully managed by AWS).

## 2. Supported Database Engines
RDS supports 6 database engines:
1.  **PostgreSQL**
2.  **MySQL**
3.  **MariaDB**
4.  **Oracle**
5.  **Microsoft SQL Server**
6.  **Amazon Aurora** (AWS proprietary, high performance, compatible with MySQL/PostgreSQL)

## 3. Why use RDS vs. DB on EC2?
Using RDS, you offload the management burden to AWS:

| Feature | RDS (Managed) | EC2 (Self-managed) |
| :--- | :--- | :--- |
| **OS Patching** | Automated | You manage it |
| **Software Install** | Pre-installed | You install/configure |
| **Backups** | Automated (Point-in-time Restore) | You confirm automation |
| **High Availability** | Multi-AZ (One click toggle) | You configure replication |
| **Scaling** | Vertical & Horizontal (Read Replicas) | You manage it |
| **Storage** | EBS (gp2, gpu3, io1...) + Auto Scaling | EBS Management |

## 4. Key Features Overview
Detailed concepts will be covered in specific sections, but here is a high-level summary:

*   **Storage Auto Scaling:**
    *   Automatically increases storage when running low (free space < 10% for 5 mins).
    *   Requires detailed **Maximum Storage Threshold**.
    *   Zero downtime.
*   **Read Replicas:** Scale **read** workload (Async replication).
*   **Multi-AZ:** High Availability & Disaster Recovery (Sync replication).
*   **Security:**
    *   **Encryption at rest** using AWS KMS.
    *   **Encryption in-transit** using SSL.
    *   **IAM Authentication** (Login without DB password).

## 5. When NOT to use RDS?
*   **Massive Analytics (OLAP):** Use **Amazon Redshift** (Data Warehouse).
*   **Key-Value / Flexible Schema:** Use **Amazon DynamoDB** (NoSQL).
*   **Unstructured Data:** Use **Amazon S3**.
*   **Need Full OS Access:** Use **EC2** or **RDS Custom**.
