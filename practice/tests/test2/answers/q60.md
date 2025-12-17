# Question 60

A company is designing a solution to collect and analyze clickstream data from a web application. The data must be available for analysis in near real-time.

Which solution meets these requirements?

## Options

A. Amazon SQS and AWS Lambda.

B. Amazon Kinesis Data Streams and Amazon OpenSearch Service.

C. Amazon S3 and Amazon Athena.

D. AWS Glue and Amazon Redshift.

## Correct Answer

**B. Amazon Kinesis Data Streams and Amazon OpenSearch Service.**

## Explanation

Amazon Kinesis Data Streams captures and processes streaming data in real-time. Amazon OpenSearch Service provides near real-time search and analytics capabilities.

### Why other options are incorrect:

- **C** - S3 + Athena is for batch analysis, not real-time.

- **D** - Glue + Redshift is for batch ETL.

- **A** - SQS + Lambda is for message processing, not analytics.

## References

- https://aws.amazon.com/kinesis/data-streams/
- https://tutorialsdojo.com/amazon-kinesis/

## Domain

Design High-Performing Architectures
