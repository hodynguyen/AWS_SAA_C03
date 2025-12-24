# Question 1

## Topic
Design High-Performing Architectures

## Question
An organization uses a Microsoft SQL Server database to support its suite of applications. The organization plans to transition to an Amazon Aurora PostgreSQL database while minimizing application code modifications.

Which combination of actions will achieve these objectives? (Select TWO.)

## Options
A. Use AWS Schema Conversion Tool (AWS SCT) to convert the database schema and AWS Database Migration Service (AWS DMS) to migrate the data.

B. Use Amazon Kinesis Data Streams for real-time data replication to Aurora PostgreSQL.

C. Use AWS AppConfig to manage configuration updates during the migration.

D. Turn on Babelfish on Aurora PostgreSQL to allow applications to continue using existing SQL queries.

E. Use AWS Glue to transform the SQL queries from the applications for compatibility with Aurora PostgreSQL.

## Correct Answer
A, D

## Explanation
AWS Schema Conversion Tool (AWS SCT) is a service that helps convert database schemas from one database engine to another. It supports conversion from various source databases, including Microsoft SQL Server, to target databases like Amazon Aurora PostgreSQL.

AWS Database Migration Service (AWS DMS) is a service that helps migrate databases to AWS quickly and securely. It supports continuous data replication with minimal downtime.

Babelfish for Aurora PostgreSQL is an extension designed for Amazon Aurora PostgreSQL. It allows the database to interpret commands from applications developed for Microsoft SQL Server. By serving as a translation layer, it converts T-SQL (Microsoft's SQL dialect) into PostgreSQL, enabling SQL Server applications to run directly on Aurora PostgreSQL with minimal or no changes required to the code.

In the given scenario, where an organization is transitioning from Microsoft SQL Server to Amazon Aurora PostgreSQL, Babelfish is a crucial tool. By turning on the Babelfish, the organization can ensure its existing applications continue functioning with minimal modifications. Babelfish will translate the SQL Server queries to be compatible with Aurora PostgreSQL. This addresses one of the primary objectives of the migration, which is to minimize application code modifications.

Furthermore, using the AWS Schema Conversion Tool (SCT) and AWS Database Migration Service (DMS) together is a logical approach. AWS SCT will handle the conversion of the Microsoft SQL Server schema to the Aurora PostgreSQL schema, while AWS DMS will facilitate the migration of data from the existing database to the new Aurora PostgreSQL database. This combination of services effectively addresses another primary goal of the migration: successfully converting the schema and migrating the data.

Hence, the correct answers are:

- Turn on Babelfish on Aurora PostgreSQL to allow applications to continue using existing SQL queries.

- Use AWS Schema Conversion Tool (AWS SCT) to convert the database schema and AWS Database Migration Service (AWS DMS) to migrate the data.

References:

https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/babelfish.html

https://docs.aws.amazon.com/SchemaConversionTool/latest/userguide/CHAP_Welcome.html

https://docs.aws.amazon.com/dms/latest/userguide/Welcome.html

Check out these AWS Database Migration Service and Amazon Aurora Cheat Sheets:

https://tutorialsdojo.com/aws-database-migration-service/

https://tutorialsdojo.com/amazon-aurora/

**Why other options are incorrect:**

- The option that says: Use AWS AppConfig to manage configuration updates during the migration is incorrect because AWS AppConfig is primarily designed to manage and deploy application configuration changes in a controlled and safe manner. It does not address the key challenges of schema conversion, data migration, or SQL query compatibility crucial for transitioning from Microsoft SQL Server to Amazon Aurora PostgreSQL.

- The option that says: Use Amazon Kinesis Data Streams for real-time data replication to Aurora PostgreSQL is incorrect. Kinesis Data Streams is typically used for real-time data ingestion and processing, not for database schema conversion or migration. While it can handle real-time data replication, it does not address the need to convert the database schema or ensure SQL query compatibility.

- The option that says: Use AWS Glue to transform the SQL queries from the applications for compatibility with Aurora PostgreSQL is incorrect. AWS Glue is primarily an extract, transform, and load (ETL) service designed for data preparation and loading for analytics. It is not intended for transforming SQL queries to ensure compatibility with a different database engine.

