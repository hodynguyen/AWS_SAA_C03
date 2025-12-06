# Question 42

A company is in the process of migrating their applications to AWS. One of their systems requires a database that can scale globally and handle frequent schema changes. The application should not have any downtime or performance issues whenever there is a schema change in the database. It should also provide a low latency response to high-traffic queries.

Which is the most suitable database solution to use to achieve this requirement?

## Options

A. An Amazon Aurora database with Read Replicas

B. Redshift

C. An Amazon RDS instance in Multi-AZ Deployments configuration

D. Amazon DynamoDB

## Correct Answer

**D. Amazon DynamoDB**

## Explanation

For applications requiring flexible schema and low-latency responses to high-traffic queries, NoSQL databases like DynamoDB are the best choice. DynamoDB:
- Has schema flexibility that lets it store complex hierarchical data within a single item
- Scales well globally
- Provides low-latency responses for high-traffic queries

Relational databases have rigid schemas and don't scale well for frequent schema changes.

### Why other options are incorrect:

- **A & C** - Aurora and RDS are relational databases with rigid schemas, not suitable for frequent schema changes.

- **B** - Redshift is primarily used for OLAP (data warehousing) systems, not for transactional workloads.

## References

- https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/bp-general-nosql-design.html
- https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/bp-relational-modeling.html
- https://tutorialsdojo.com/amazon-dynamodb

## Domain

Design Secure Applications and Architectures
