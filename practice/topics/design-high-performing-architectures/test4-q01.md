# Question 1

A company uses Microsoft SQL Server and plans to migrate to Amazon Aurora PostgreSQL while minimizing application code changes.

Which combination of actions will achieve these objectives? (Select TWO.)

## Options

A. Use AWS Schema Conversion Tool (AWS SCT) to convert the database schema and AWS Database Migration Service (AWS DMS) to migrate the data.

B. Use Amazon Kinesis Data Streams for real-time data replication to Aurora PostgreSQL.

C. Use AWS AppConfig to manage configuration updates during the migration.

D. Turn on Babelfish on Aurora PostgreSQL to allow applications to continue using existing SQL queries.

E. Use AWS Glue to transform the SQL queries from the applications for compatibility with Aurora PostgreSQL.

## Correct Answer

**A. Use AWS Schema Conversion Tool (AWS SCT) to convert the database schema and AWS Database Migration Service (AWS DMS) to migrate the data.**

**D. Turn on Babelfish on Aurora PostgreSQL to allow applications to continue using existing SQL queries.**

## Explanation

Babelfish for Aurora PostgreSQL is a translation layer that allows the database to interpret T-SQL (SQL Server's dialect) commands, enabling SQL Server applications to run on Aurora PostgreSQL with minimal code changes.

AWS SCT converts the database schema from SQL Server to PostgreSQL format, while AWS DMS handles the actual data migration with minimal downtime.

### Why other options are incorrect:

- **B** - Kinesis Data Streams is for real-time data ingestion/processing, not database migration or schema conversion.

- **C** - AWS AppConfig manages application configuration deployments, not database migrations.

- **E** - AWS Glue is an ETL service for data preparation, not for transforming SQL queries.

## References

- https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/babelfish.html
- https://docs.aws.amazon.com/SchemaConversionTool/latest/userguide/CHAP_Welcome.html
- https://tutorialsdojo.com/aws-database-migration-service/

## Domain

Design High-Performing Architectures
