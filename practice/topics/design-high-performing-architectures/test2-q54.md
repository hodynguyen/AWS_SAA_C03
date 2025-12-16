# Question 54

A company runs an e-commerce application that experiences variable traffic. During peak periods, customers experience slow response times when the application writes data to the database. The company uses Amazon RDS MySQL.

Which solution will improve write performance?

## Options

A. Enable RDS Multi-AZ deployment.

B. Add read replicas to the RDS instance.

C. Migrate to Amazon Aurora with multiple writer endpoints.

D. Increase the RDS instance size.

## Correct Answer

**D. Increase the RDS instance size.**

## Explanation

For write-heavy workloads, scaling up the instance size provides more compute capacity, memory, and I/O throughput, directly improving write performance.

### Why other options are incorrect:

- **A** - Multi-AZ is for availability, not write performance.

- **B** - Read replicas help reads, not writes.

- **C** - Aurora multi-writer has limitations and complexity.

## References

- https://aws.amazon.com/rds/mysql/
- https://tutorialsdojo.com/amazon-relational-database-service-amazon-rds/

## Domain

Design High-Performing Architectures
