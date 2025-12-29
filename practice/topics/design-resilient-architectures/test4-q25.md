# Question 25

A Solutions Architect needs to design an RDS MySQL database with automatic failover for high availability.

Which action should be taken?

## Options

A. Create a standby replica in another AZ by enabling Multi-AZ deployment.

B. Create five read replicas across different AZs. Promote a replica during failover.

C. Create five cross-region read replicas. Promote a replica during failover.

D. Create read replicas in same and different regions. Promote a replica during failover.

## Correct Answer

**A. Create a standby replica in another AZ by enabling Multi-AZ deployment.**

## Explanation

RDS Multi-AZ deployment automatically:
1. Creates a synchronous standby replica in a different AZ
2. Handles automatic failover (typically 60-120 seconds)
3. Updates DNS endpoint to point to the new primary

No manual intervention required—failover is fully automated.

### Why other options are incorrect:

- **B, C, D** - Read replicas require manual promotion to become primary. They don't support automatic failover like Multi-AZ standby instances.

## References

- https://aws.amazon.com/rds/features/multi-az/
- https://tutorialsdojo.com/amazon-relational-database-service-amazon-rds/

## Domain

Design Resilient Architectures
