# Question 37

A global news website uses MySQL RDS with millions of viewers. The database has a read-heavy workload with ACID compliance requirements.

What is the best option to increase read throughput?

## Options

A. Enable Multi-AZ deployments.

B. Enable Amazon RDS Standby Replicas.

C. Use SQS to queue up the requests.

D. Enable Amazon RDS Read Replicas.

## Correct Answer

**D. Enable Amazon RDS Read Replicas.**

## Explanation

Read Replicas offload read traffic from the primary:
- **Asynchronous replication**: Near real-time data copies
- **Multiple replicas**: Create up to 5 (15 for Aurora) to distribute reads
- **Same ACID guarantees**: Primary handles writes, replicas handle reads

### Why other options are incorrect:

- **A** - Multi-AZ provides high availability/failover, not read scaling.

- **B** - Standby replicas (Multi-AZ) cannot be queried—they're for failover only.

- **C** - SQS queues requests but doesn't increase database read throughput.

## References

- https://aws.amazon.com/rds/details/read-replicas/
- https://tutorialsdojo.com/amazon-relational-database-service-amazon-rds/

## Domain

Design High-Performing Architectures
