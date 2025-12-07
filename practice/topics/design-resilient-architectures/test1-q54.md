# Question 54

A Forex trading platform, which frequently processes and stores global financial data every minute, is hosted in an on-premises data center and uses an Oracle database. Due to a recent cooling problem in its data center, the company urgently needs to migrate its infrastructure to AWS to improve the performance of its applications.

Which combination of actions would meet the requirement? (Select TWO.)

## Options

A. Create an Oracle database in Amazon RDS with Multi-AZ deployments.

B. Migrate the Oracle database to AWS using the AWS Database Migration Service

C. Convert the database schema using the AWS Schema Conversion Tool.

D. Migrate the Oracle database to a non-cluster Amazon Aurora with a single instance.

E. Launch an Oracle database instance in Amazon RDS with Recovery Manager (RMAN) enabled.

## Correct Answers

**A. Create an Oracle database in Amazon RDS with Multi-AZ deployments.**

**B. Migrate the Oracle database to AWS using the AWS Database Migration Service**

## Explanation

For high availability, use RDS Multi-AZ which provides automatic failover to a standby replica in a different Availability Zone.

AWS DMS makes it easy to move on-premises databases to AWS with minimal downtime. For homogeneous migrations (Oracle to Oracle), no schema conversion is needed.

### Why other options are incorrect:

- **E** - Oracle RMAN is not supported in RDS.

- **C** - AWS SCT is for heterogeneous migrations (e.g., Oracle to PostgreSQL). This is an Oracle-to-Oracle migration.

- **D** - A single-instance Aurora doesn't provide high availability for mission-critical applications.

## References

- https://aws.amazon.com/rds/details/multi-az/
- https://aws.amazon.com/dms/
- https://tutorialsdojo.com/amazon-relational-database-service-amazon-rds/

## Domain

Design Resilient Architectures
