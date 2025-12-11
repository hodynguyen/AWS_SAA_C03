# Question 14

An online events registration system is hosted in AWS and uses ECS to host its front-end tier and an RDS configured with Multi-AZ for its database tier. What are the events that will make Amazon RDS automatically perform a failover to the standby replica? (Select TWO.)

## Options

A. Loss of availability in primary Availability Zone

B. Compute unit failure on secondary DB instance

C. Storage failure on secondary DB instance

D. Storage failure on primary

E. In the event of Read Replica failure

## Correct Answers

**A. Loss of availability in primary Availability Zone**

**D. Storage failure on primary**

## Explanation

Amazon RDS automatically performs a failover in the event of any of the following:
- Loss of availability in primary Availability Zone
- Loss of network connectivity to primary
- Compute unit failure on primary
- Storage failure on primary

### Why other options are incorrect:

- **B, C** - Failures on secondary don't trigger failover.

- **E** - Read Replica failure doesn't trigger Multi-AZ failover.

## References

- https://aws.amazon.com/rds/details/multi-az/
- https://tutorialsdojo.com/amazon-relational-database-service-amazon-rds/

## Domain

Design Secure Architectures
