# Question 44

A single Aurora instance is used for a trading platform. What happens during failover with no replicas?

## Options

A. Aurora flips A record to healthy replica.

B. Aurora creates new instance in same AZ on best-effort basis.

C. Aurora flips CNAME to healthy replica.

D. Aurora creates new instance in different AZ first.

## Correct Answer

**B. Aurora creates new instance in same AZ on best-effort basis.**

## Explanation

Aurora failover behavior (single instance, no replicas):
- **Best-effort recreation**: Tries to create in same AZ
- **Not guaranteed**: May fail if AZ has issues
- **Recommendation**: Use replicas for HA

With replicas, Aurora flips CNAME to healthy replica (30s failover).

### Why other options are incorrect:

- **A, C** - These apply when replicas exist (CNAME flip, not A record).

- **D** - First attempts same AZ, then different AZ if unsuccessful.

## References

- https://aws.amazon.com/rds/aurora/faqs/
- https://tutorialsdojo.com/amazon-aurora/

## Domain

Design Resilient Architectures
