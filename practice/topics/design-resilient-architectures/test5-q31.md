# Question 31

A heterogeneous database migration from on-premises Oracle to AWS PostgreSQL requires schema and code transformation.

Which is the most suitable approach?

## Options

A. Use Amazon Neptune then AWS Batch for migration.

B. Use Launch Template for conversion then DMS.

C. Heterogeneous migrations not supported in AWS.

D. Use AWS Schema Conversion Tool then AWS DMS.

## Correct Answer

**D. Use AWS Schema Conversion Tool then AWS DMS.**

## Explanation

Two-step process:
1. **AWS SCT**: Converts Oracle schema/code to PostgreSQL format
2. **AWS DMS**: Migrates data with automatic type conversion

SCT handles the heterogeneous schema differences before DMS moves the data.

### Why other options are incorrect:

- **A** - Neptune is graph database, not for relational schema conversion.

- **B** - Launch Templates configure EC2, not database conversion.

- **C** - False. AWS fully supports heterogeneous migrations with SCT + DMS.

## References

- https://aws.amazon.com/dms/
- https://tutorialsdojo.com/aws-database-migration-service/

## Domain

Design Resilient Architectures
