# Question 10

A company is experiencing repeated outages in the Availability Zone where its Amazon RDS database instance is deployed, resulting in a complete loss of access to the database during each incident.

Which solution should be implemented to prevent losing database access if this occurs again?

## Options

A. Enable Multi-AZ failover

B. Create a read replica

C. Make a snapshot of the database

D. Increase the database instance size

## Correct Answer

**A. Enable Multi-AZ failover**

## Explanation

Amazon RDS Multi-AZ deployments are designed to enhance the availability and durability of database instances, making them well-suited for production workloads. When you enable Multi-AZ failover, Amazon RDS automatically creates a standby replica in a different Availability Zone (AZ) and synchronously replicates data from the primary instance. This ensures high data consistency and protection against infrastructure-related disruptions.

In the event of planned maintenance or an unexpected failure such as an Availability Zone outage or hardware issue, Amazon RDS automatically performs a failover to the standby instance. This process is fully managed by Amazon RDS and does not require manual intervention.

### Why other options are incorrect:

- **C** - Snapshots are typically used for backup and disaster recovery, not for maintaining high availability. A snapshot allows you to restore a database to a specific point in time, but it does not prevent downtime.

- **D** - Increasing the database instance size improves compute and memory capacity, but does not address Availability Zone-level failures.

- **B** - Read replicas are primarily intended to handle read-heavy workloads and do not automatically take over in the event of a failure. Promoting a read replica requires manual intervention.

## References

- https://aws.amazon.com/rds/features/multi-az/
- https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.MultiAZ.html
- https://tutorialsdojo.com/amazon-relational-database-service-amazon-rds/

## Domain

Design Resilient Architectures
