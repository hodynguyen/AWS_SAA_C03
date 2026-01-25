# RDS Custom for Oracle and Microsoft SQL Server

## 1. What is RDS Custom?
RDS Custom is a managed database service used for applications that require access to the **underlying Operating System (OS)** and database environment customization.
- It bridges the gap between **Amazon RDS** (fully managed, no OS access) and **EC2** (self-managed, full OS access).
- You get the benefits of RDS automation (patching, backups) but retain the ability to customize the OS.

## 2. Supported Engines
RDS Custom is currently available for:
1.  **Oracle**
2.  **Microsoft SQL Server**

## 3. When to use RDS Custom?
Use RDS Custom when your application requires:
- **OS Access:** You need to SSH (Linux) or RDP (Windows) into the server.
- **Custom Software:** You need to install legacy applications, third-party agents, or custom drivers on the same server as the database.
- **Specific Configurations:** You need to modify OS kernel settings or database configurations that are not exposed in standard RDS.

## 4. Responsibility Model
With RDS Custom, the shared responsibility shifts slightly:
- **AWS Responsibility:** Infrastructure, hardware, automated backups, and providing the automation tools.
- **Your Responsibility:**
    - Managing the OS customization.
    - Ensuring your customizations do not break the AWS automation (e.g., if you turn off the automation agent, backups might stop).
    - Managing snapshots of your customizations.

## 5. Summary Comparison

| Feature | RDS Standard | RDS Custom | EC2 |
| :--- | :--- | :--- | :--- |
| **OS Access** | No | **Yes** (SSH/RDP) | Yes |
| **Management** | Fully Managed | Managed but requires care | Self Managed |
| **Engines** | All 6 engines | Oracle & SQL Server | Any |
| **Use Case** | Most modern apps | Legacy apps needing OS access | Full control required |
