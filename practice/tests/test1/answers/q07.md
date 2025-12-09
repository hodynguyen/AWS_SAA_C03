# Question 7

A Solutions Architect is designing a highly available relational database solution to mitigate the risk of a multi-region failure. The database must meet a Recovery Point Objective (RPO) of 1 second and a Recovery Time Objective (RTO) of less than 1 minute. The architect needs a disaster recovery plan that enables automatic cross-region replication with minimal data loss and rapid recovery in the event of a failure.

Which AWS feature best fulfills this requirement?

## Options

A. Amazon Aurora Global Database

B. Amazon DynamoDB Global table

C. Amazon Timestream for Analytics

D. Amazon RDS for PostgreSQL with cross-region read replicas

## Correct Answer

**A. Amazon Aurora Global Database**

## Explanation

Amazon Aurora Global Database is designed for globally distributed applications, allowing a single Amazon Aurora database to span multiple AWS regions. It replicates your data with no impact on database performance, enables fast local reads with low latency in each region, and provides disaster recovery from region-wide outages.

Aurora Global Database supports storage-based replication that has a latency of less than 1 second. If there is an unplanned outage, one of the secondary regions you assigned can be promoted to read and write capabilities in less than 1 minute. This feature is called Cross-Region Disaster Recovery.

An RPO of 1 second and an RTO of less than 1 minute provide you a strong foundation for a global business continuity plan.

### Why other options are incorrect:

- **B** - While DynamoDB Global Tables support multi-region, fully replicated tables with low latency, it's more suitable for NoSQL workloads, not relational databases.

- **D** - Replication lag in cross-region read replicas can take several minutes to complete, which could prevent meeting the RPO of 1 second.

- **C** - Amazon Timestream is a serverless time series database service commonly used for IoT and operational applications, not for this use case.

## References

- https://aws.amazon.com/rds/aurora/global-database/
- https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/aurora-global-database.html
- https://tutorialsdojo.com/amazon-aurora/

## Domain

Design Resilient Architectures
