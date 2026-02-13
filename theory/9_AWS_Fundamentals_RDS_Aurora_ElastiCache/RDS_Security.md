# RDS Security

## 1. Encryption

### At-rest Encryption
- **Capabilities**:
  - Encrypts master and read replicas.
  - Encrypts Storage (EBS Volume).
  - Encrypts Automated Backups, Read Replicas, and Snapshots.
- **Mechanism**: Uses **AWS KMS** (AES-256).
- **Important**: Must be defined at **launch time**.
- **Fixed Issue**: If you create a DB without encryption, you **cannot** enable it later directly.

### Encrypting an Existing Unencrypted RDS Database
To encrypt an unencrypted database, follow this workflow:
1. **Create a Snapshot** of the unencrypted database instance.
2. **Copy the Snapshot** and enable encryption for the copy (select a KMS key).
3. **Restore the Database** from the encrypted snapshot.
4. **Switch Applications** to the new encrypted database instance (update connection strings).
5. **Delete** the old unencrypted instance (optional).

### In-transit Encryption
- AWS RDS supports **SSL/TLS** encryption for data in transit.
- Clients must use the AWS root certificate bundle (`rds-ca-bundle.pem`) to verify the connection.
- **Enforcement**:
  - PostgreSQL: `rds.force_ssl=1` in the parameter group.
  - MySQL: `Grant USAGE ON *.* TO 'mysqluser'@'%' REQUIRE SSL;`.

## 2. Network Security
- **VPC**: RDS instances should be deployed in a **Private Subnet**.
- **Security Groups**: Control network access.
  - **Inbound Rules**: Allow traffic only from trusted sources (e.g., Application Security Group, Bastion Host).
  - **Port**: 3306 (MySQL), 5432 (Postgres), 1433 (SQL Server), 1521 (Oracle).

## 3. Access Control
- **IAM Database Authentication**:
  - Use IAM Roles/Users to authenticate instead of passwords.
  - Works with MySQL and PostgreSQL.
  - Token-based (token validity: 15 minutes).
  - **Benefits**: No hardcoded passwords, centralized management.
- **Traditional Auth**: Username/Password (can be managed/rotated by **AWS Secrets Manager**).
