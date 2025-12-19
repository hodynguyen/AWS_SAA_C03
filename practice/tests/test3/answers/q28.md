# Question 28

## Topic
Design High-Performing Architectures

## Question
Due to the large volume of query requests, the database performance of an online reporting application significantly slowed down. The Solutions Architect is trying to convince her client to use Amazon RDS Read Replica for their application instead of setting up a Multi-AZ Deployments configuration.

What are two benefits of using Read Replicas over Multi-AZ that the Architect should point out? (Select TWO.)

## Options
A. It enhances the read performance of your primary database by increasing its IOPS and accelerates its query processing via AWS Global Accelerator.

B. Provides asynchronous replication and improves the performance of the primary database by taking read-heavy database workloads from it.

C. Allows both read and write operations on the read replica to complement the primary database.

D. Provides synchronous replication and automatic failover in the case of Availability Zone service failures.

E. It elastically scales out beyond the capacity constraints of a single DB instance for read-heavy database workloads.

## Correct Answers
**B. Provides asynchronous replication and improves the performance of the primary database by taking read-heavy database workloads from it.**

**E. It elastically scales out beyond the capacity constraints of a single DB instance for read-heavy database workloads.**

## Explanation
Amazon RDS Read Replicas provide enhanced performance and durability for database instances. This feature makes it easy to elastically scale out beyond the capacity constraints of a single DB instance for read-heavy database workloads.

Read replicas use the engines' native asynchronous replication to offload read traffic from the primary database.

**Why other options are incorrect:**
- **Option A** is incorrect because Read Replicas don't increase primary DB IOPS or use Global Accelerator.
- **Option C** is incorrect because Read Replicas are read-only by default.
- **Option D** is incorrect because this is a benefit of Multi-AZ, not Read Replicas.

## References
- https://aws.amazon.com/rds/details/read-replicas/
- https://aws.amazon.com/rds/features/multi-az/
- https://tutorialsdojo.com/amazon-relational-database-service-amazon-rds/
