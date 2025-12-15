# Question 45

A company is migrating an on-premises Oracle database to Amazon RDS for Oracle. The database handles mission-critical workloads and the company wants the migration to involve minimal downtime.

Which service should be used to migrate the database?

## Options

A. AWS Database Migration Service (DMS).

B. AWS DataSync.

C. AWS Snowball Edge.

D. Amazon Kinesis Data Firehose.

## Correct Answer

**A. AWS Database Migration Service (DMS).**

## Explanation

AWS DMS helps you migrate databases to AWS quickly and securely with minimal downtime. It supports ongoing replication to keep source and target in sync.

### Why other options are incorrect:

- **B** - DataSync is for file/object storage, not databases.

- **C** - Snowball is for large data transfers, not database migration.

- **D** - Kinesis Firehose is for streaming data delivery.

## References

- https://aws.amazon.com/dms/
- https://tutorialsdojo.com/aws-database-migration-service/

## Domain

Design Resilient Architectures
