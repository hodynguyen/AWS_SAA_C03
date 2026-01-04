# Question 21

Reserved EC2 with 90% CPU, RDS Multi-AZ for prod/test/dev.

How to reduce cost without affecting availability?

## Options

A. Use Spot instead of Reserved.

B. Use On-demand instead of Reserved.

C. Don't use Multi-AZ for dev/test databases.

D. Remove Elastic Load Balancer.

## Correct Answer

**C. Don't use Multi-AZ for dev/test databases.**

## Explanation

Multi-AZ cost optimization:
- **Production**: Keep Multi-AZ for HA
- **Dev/Test**: Single-AZ sufficient
- **Cost savings**: Multi-AZ doubles RDS cost
- **Non-critical**: Dev/test can tolerate downtime

### Why other options are incorrect:

- **A** - Spot can be terminated; bad for production.

- **B** - On-demand more expensive than Reserved.

- **D** - ELB is crucial for elasticity and reliability.

## References

- https://aws.amazon.com/rds/details/multi-az/
- https://tutorialsdojo.com/amazon-relational-database-service-amazon-rds/

## Domain

Design Resilient Architectures
