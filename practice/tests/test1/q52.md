# Question 52

A healthcare organization wants to build a system that can predict drug prescription abuse. The organization will gather real-time data from multiple sources, which include Personally Identifiable Information (PII). It's crucial that this sensitive information is anonymized prior to landing in a NoSQL database for further processing.

Which solution would meet the requirements?

## Options

A. Create a data lake in Amazon S3 and use it as the primary storage for patient health data. Use an S3 trigger to run an AWS Lambda function that performs anonymization.

B. Ingest real-time data using Amazon Kinesis Data Stream. Use an AWS Lambda function to anonymize the PII, then store it in Amazon DynamoDB.

C. Deploy an Amazon Data Firehose stream to capture and transform the streaming data. Deliver the anonymized data to Amazon Redshift for analysis.

D. Stream the data in an Amazon DynamoDB table. Enable DynamoDB Streams, and configure an AWS Lambda function to perform anonymization on newly written items.

## Correct Answer

**B. Ingest real-time data using Amazon Kinesis Data Stream. Use an AWS Lambda function to anonymize the PII, then store it in Amazon DynamoDB.**

## Explanation

Amazon Kinesis Data Streams integrates with AWS Lambda, which can transform and anonymize PII in transit before storage. This ensures sensitive information is anonymized immediately, preventing unanonymized PII from being stored.

DynamoDB is a NoSQL database suitable for handling the processed data.

### Why other options are incorrect:

- **A** - This stores unanonymized PII in S3 before anonymization, violating the requirement.

- **D** - DynamoDB Streams processes already-written data, meaning unanonymized PII is stored first.

- **C** - Amazon Redshift is not a NoSQL database as required.

## References

- https://aws.amazon.com/kinesis/data-streams/
- https://docs.aws.amazon.com/lambda/latest/dg/with-kinesis.html
- https://tutorialsdojo.com/amazon-kinesis/

## Domain

Design High-Performing Architectures
