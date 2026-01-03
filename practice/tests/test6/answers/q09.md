# Question 9

Cryptocurrency app going global. Need highly available database in multiple regions.

What are the benefits of RDS Multi-AZ? (Select TWO.)

## Options

A. Provides SQL optimization.

B. Replicates to different region.

C. Increased availability during OS patching and DB scaling.

D. Significantly increases database performance.

E. Enhanced durability during AZ outages.

## Correct Answer

**C. Increased availability during OS patching and DB scaling.**

**E. Enhanced durability during AZ outages.**

## Explanation

RDS Multi-AZ benefits:
- **High availability**: Automatic failover to standby
- **Durability**: Synchronous replication to different AZ
- **Maintenance**: No downtime during patching
- **Same region**: Standby is in different AZ, same region

### Why other options are incorrect:

- **A, D** - Multi-AZ doesn't improve performance or SQL.

- **B** - Multi-AZ is within same region, not cross-region.

## References

- https://aws.amazon.com/rds/details/multi-az/
- https://tutorialsdojo.com/amazon-relational-database-service-amazon-rds/

## Domain

Design Resilient Architectures
