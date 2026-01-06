# Question 49

Online learning portal with Aurora. How to improve availability?

## Options

A. Use Asynchronous Key Prefetch.

B. Create Aurora Replicas.

C. Deploy Aurora to EC2 Auto Scaling.

D. Enable Hash Joins.

## Correct Answer

**B. Create Aurora Replicas.**

## Explanation

Aurora Replicas for HA:
- **Up to 15 replicas**: Across AZs
- **Automatic failover**: Promote replica if primary fails
- **Same storage**: Shared cluster volume
- **Read scaling**: Offload reads to replicas

### Why other options are incorrect:

- **A** - Key Prefetch for query performance.

- **C** - Aurora is managed; not on EC2.

- **D** - Hash Joins for query performance.

## References

- https://aws.amazon.com/rds/aurora/faqs/
- https://tutorialsdojo.com/amazon-aurora/

## Domain

Design Resilient Architectures
