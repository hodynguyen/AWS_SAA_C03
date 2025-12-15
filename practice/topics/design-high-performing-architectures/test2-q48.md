# Question 48

A solutions architect is designing a solution to store and analyze log files from a web application across multiple servers. The log files should be aggregated in near real-time and subsequently stored in a data lake for batch analysis.

Which solution meets these requirements?

## Options

A. Use Amazon Kinesis Data Firehose to collect and deliver the log data to Amazon S3.

B. Install CloudWatch agent on each server and send logs to Amazon RDS.

C. Use AWS Data Pipeline to transfer log files to Amazon Redshift.

D. Set up Amazon SQS queues to aggregate logs and write to Amazon DynamoDB.

## Correct Answer

**A. Use Amazon Kinesis Data Firehose to collect and deliver the log data to Amazon S3.**

## Explanation

Amazon Kinesis Data Firehose is the easiest way to capture, transform, and load streaming data into data lakes (S3), data stores, and analytics services.

### Why other options are incorrect:

- **B** - RDS is not a data lake.

- **C** - Data Pipeline is for batch ETL, not real-time.

- **D** - SQS + DynamoDB is not ideal for log analytics.

## References

- https://aws.amazon.com/kinesis/data-firehose/
- https://tutorialsdojo.com/amazon-kinesis/

## Domain

Design High-Performing Architectures
