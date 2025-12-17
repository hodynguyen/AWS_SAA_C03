# Question 65

A company is designing an application that requires a highly available relational database. The database should automatically handle read scaling and failover.

Which solution provides these capabilities with least operational overhead?

## Options

A. Amazon RDS for MySQL with Multi-AZ and read replicas.

B. Amazon Aurora with Auto Scaling for read replicas.

C. Amazon DynamoDB with global tables.

D. Amazon Redshift with concurrency scaling.

## Correct Answer

**B. Amazon Aurora with Auto Scaling for read replicas.**

## Explanation

Amazon Aurora provides built-in high availability with Multi-AZ, automatic failover, and Auto Scaling for read replicas. It requires minimal operational overhead compared to manual read replica management.

### Why other options are incorrect:

- **A** - RDS requires manual read replica management.

- **C** - DynamoDB is NoSQL, not relational.

- **D** - Redshift is for data warehousing.

## References

- https://aws.amazon.com/rds/aurora/
- https://tutorialsdojo.com/amazon-aurora/

## Domain

Design Resilient Architectures
