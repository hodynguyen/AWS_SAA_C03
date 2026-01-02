# Question 65

50 TB OLTP database migration. Must be ACID-compliant, handle complex queries, and scale to grow.

Which database service should be used?

## Options

A. Amazon Redshift

B. Amazon DynamoDB

C. Amazon RDS

D. Amazon Aurora

## Correct Answer

**D. Amazon Aurora**

## Explanation

Amazon Aurora:
- **ACID-compliant**: Full relational database
- **OLTP optimized**: 5x MySQL, 3x PostgreSQL performance
- **Auto-scaling storage**: Up to 128 TiB
- **Complex queries**: Full SQL support
- **Managed**: Automated backups, failover, maintenance

### Why other options are incorrect:

- **A** - Redshift is for OLAP, not OLTP.

- **B** - DynamoDB is NoSQL; limited complex queries.

- **C** - RDS has 16 TB table limit; Aurora scales better.

## References

- https://aws.amazon.com/rds/aurora/
- https://tutorialsdojo.com/amazon-aurora/

## Domain

Design Resilient Architectures
