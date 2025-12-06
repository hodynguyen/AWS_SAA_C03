# Question 45

An application that records weather data every minute is deployed in a fleet of Amazon EC2 Spot instances and uses a MySQL RDS database instance. Currently, there is only one Amazon RDS instance running in one Availability Zone. The database needs to be improved to ensure high availability by enabling synchronous data replication to another RDS instance.

Which of the following performs synchronous data replication in RDS?

## Options

A. RDS Read Replica

B. Amazon CloudFront running as a Multi-AZ deployment

C. RDS DB instance running as a Multi-AZ deployment

D. Amazon DynamoDB Read Replica

## Correct Answer

**C. RDS DB instance running as a Multi-AZ deployment**

## Explanation

When you create or modify your DB instance to run as a Multi-AZ deployment, Amazon RDS automatically provisions and maintains a synchronous standby replica in a different Availability Zone. Updates to your DB Instance are synchronously replicated across Availability Zones to keep both in sync.

### Why other options are incorrect:

- **A** - Read Replica provides asynchronous replication, not synchronous.

- **D** - DynamoDB does not offer a Read Replica feature. It uses global tables for replication.

- **B** - CloudFront does not have a Read Replica feature. It caches content at edge locations.

## References

- https://aws.amazon.com/rds/details/multi-az/
- https://aws.amazon.com/rds/features/multi-az/
- https://tutorialsdojo.com/amazon-relational-database-service-amazon-rds/

## Domain

Design Secure Applications and Architectures
