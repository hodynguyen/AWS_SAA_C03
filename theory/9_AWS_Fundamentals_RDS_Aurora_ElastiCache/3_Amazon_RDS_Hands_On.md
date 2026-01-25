# Amazon RDS Hands-On (Configuration & Best Practices)

When creating an Amazon RDS Instance, you need to understand the following configuration options to architect correctly.

## 1. Creation Method
- **Standard Create:** Allows full configuration (Availability, Security, Backups, Maintenance). **Recommended** for understanding all options.
- **Easy Create:** Uses best-practice defaults. Good for quick testing but hides many options.

## 2. DB Instance Classes
- **Standard Classes (m5, m6g):** Balance of compute and memory. General purpose.
- **Memory Optimized (r5, r6g):** More RAM. Best for production workloads with heavy datasets.
- **Burstable Classes (t3, t4g):** Cheaper, can burst CPU usage. Suitable for Dev/Test.

## 3. Storage Configuration
- **Storage Type:**
    - **General Purpose SSD (gp2/gp3):** Cost-effective, suitable for most workloads.
    - **Provisioned IOPS SSD (io1/io2):** High performance, low latency. Expensive. Used for mission-critical apps.
- **Storage Autoscaling:**
    - Essential feature to prevent "Disk Full" errors.
    - You set a **Maximum Storage Threshold** (e.g., 1000 GB).
    - RDS automatically scales up storage when free space is low.

## 4. Connectivity (Network & Security)
- **VPC:** Select the Virtual Private Cloud where the DB resides.
- **Subnet Group:** Defines which Subnets (and AZs) the DB can be placed in.
- **Public Access:**
    - **No (Best Practice):** DB gets a Private IP. Only accessible from within the VPC (e.g., from an EC2 instance or Lambda).
    - **Yes:** DB gets a Public IP. Accessible from the internet (high security risk).
- **VPC Security Group:** Acts as a firewall.
    - You must allow inbound traffic on the DB port (3306 for MySQL, 5432 for Postgres).
    - **Source:** Should be the Security Group ID of your Application (EC2/Lambda), **NOT** `0.0.0.0/0`.

## 5. Database Authentication
- **Password Authentication:** Traditional username/password.
- **Password and IAM Database Authentication:**
    - Use IAM Roles/Users to authenticate.
    - Identity is managed by AWS IAM (centralized).
    - Token-based login (token expires in 15 mins).
    - Supported by MySQL and PostgreSQL.

## 6. Additional Configuration
- **Metric Monitoring:** Enable "Enhanced Monitoring" to see granular OS-level metrics (CPU processes).
- **Deleton Protection:** Prevents accidental deletion of the database. You must modify the DB and disable this before you can delete it.
- **Maintenance Window:** Specify when AWS can perform OS/DB updates.
