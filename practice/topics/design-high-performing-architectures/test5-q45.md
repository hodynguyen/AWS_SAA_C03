# Question 45

Kinesis Data Streams processes stock data. Where can consumers store results? (Select TWO.)

## Options

A. Amazon Athena

B. Amazon S3

C. Amazon EMR

D. AWS Glue

E. Amazon Redshift

## Correct Answer

**B. Amazon S3**

**E. Amazon Redshift**

## Explanation

Kinesis consumers can store results to:
- **Amazon S3**: Object storage for any data
- **Amazon Redshift**: Data warehouse for analytics
- **DynamoDB**: Also supported (not in options)

### Why other options are incorrect:

- **A** - Athena queries S3; not a storage destination.

- **C** - EMR is processing, not storage.

- **D** - Glue is ETL service, not storage.

## References

- http://docs.aws.amazon.com/streams/latest/dev/key-concepts.html
- https://tutorialsdojo.com/amazon-kinesis/

## Domain

Design High-Performing Architectures
