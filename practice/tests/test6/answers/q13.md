# Question 13

RDS MySQL 5.6 Multi-AZ with slow reads from secondary region. Need <1 second replication latency.

Which option provides this?

## Options

A. Upgrade MySQL engine.

B. Create RDS MySQL read replica in secondary region.

C. Migrate to Aurora and create cross-region read replica.

D. Use ElastiCache to improve performance.

## Correct Answer

**C. Migrate to Aurora and create cross-region read replica.**

## Explanation

Aurora replication:
- **Sub-second replication**: Up to 15 replicas
- **Cross-region**: Global Database feature
- **5x faster**: Than standard MySQL
- **Auto-failover**: To any replica

### Why other options are incorrect:

- **A** - Engine upgrade doesn't improve replication latency.

- **B** - MySQL replica has seconds of lag, not sub-second.

- **D** - ElastiCache for caching, not replication latency.

## References

- https://aws.amazon.com/rds/aurora/faqs/
- https://tutorialsdojo.com/amazon-aurora/

## Domain

Design High-Performing Architectures
