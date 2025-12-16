# Question 50

A company is running a three-tier architecture on AWS with a web tier, application tier, and database tier. The application requires low latency and the ability to handle thousands of concurrent connections to a MySQL database.

Which solution provides the LOWEST latency for database operations?

## Options

A. Enable Multi-AZ deployment for the RDS instance.

B. Create an Amazon ElastiCache cluster in front of the RDS instance.

C. Enable RDS read replicas.

D. Migrate to Amazon Aurora with provisioned capacity.

## Correct Answer

**B. Create an Amazon ElastiCache cluster in front of the RDS instance.**

## Explanation

Amazon ElastiCache provides in-memory caching that delivers microsecond latency for frequently accessed data, significantly reducing load on the database.

### Why other options are incorrect:

- **A** - Multi-AZ is for availability, not latency.

- **C** - Read replicas help scale reads but don't reduce latency.

- **D** - Aurora improves performance but not as much as caching.

## References

- https://aws.amazon.com/elasticache/
- https://tutorialsdojo.com/amazon-elasticache/

## Domain

Design High-Performing Architectures
