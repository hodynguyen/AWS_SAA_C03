# Question 32

An OLTP application uses RDS. The Data Analytics team needs to run queries without impacting production performance.

What is the most suitable and cost-effective solution?

## Options

A. Upgrade RDS instance to a larger type.

B. Set up an RDS Read Replica. Direct analytics queries to the replica.

C. Set up Multi-AZ deployment. Direct queries to the standby instance.

D. Migrate to Amazon Redshift for analytics.

## Correct Answer

**B. Set up an RDS Read Replica. Direct analytics queries to the replica.**

## Explanation

Read Replicas offload read traffic from the primary database:
- **Asynchronous replication**: Near real-time data for analytics
- **Separate endpoint**: Analytics queries don't impact production
- **Cost-effective**: Only pay for the replica instance

Perfect for read-heavy workloads without affecting OLTP performance.

### Why other options are incorrect:

- **A** - Upgrading is expensive and doesn't isolate analytics queries from production.

- **C** - Multi-AZ standby instances cannot be queried directly.

- **D** - Redshift is for OLAP, not OLTP. Migration is unnecessary for this use case.

## References

- https://aws.amazon.com/rds/details/read-replicas/
- https://tutorialsdojo.com/amazon-relational-database-service-amazon-rds/

## Domain

Design High-Performing Architectures
