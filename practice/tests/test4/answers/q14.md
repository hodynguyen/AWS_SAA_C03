# Question 14

A company received a CSV data export from a third-party analytics tool and stored it in S3. The manager needs to validate the data.

What is the most cost-effective and easiest way to analyze the data using standard SQL?

## Options

A. Create a migration tool to load the CSV to DynamoDB. Run queries using DynamoDB.

B. Use AWS Athena to analyze the export data file in S3.

C. Use mysqldump to load the CSV to MySQL RDS. Run SQL queries after loading.

D. Use a migration tool to load the CSV to Redshift. Run queries after loading.

## Correct Answer

**B. Use AWS Athena to analyze the export data file in S3.**

## Explanation

Amazon Athena is a serverless query service that analyzes data directly in S3 using standard SQL. No infrastructure setup required—just point Athena at your S3 data and query immediately. You pay only for the data scanned, making it the most cost-effective option for ad-hoc queries.

### Why other options are incorrect:

- **A** - DynamoDB is a NoSQL database, not designed for SQL queries on CSV data.

- **C** - Setting up RDS just for validation adds unnecessary cost and complexity.

- **D** - Redshift requires cluster provisioning and data loading—overkill for simple validation.

## References

- https://docs.aws.amazon.com/athena/latest/ug/what-is.html
- https://tutorialsdojo.com/amazon-athena/

## Domain

Design Secure Architectures
