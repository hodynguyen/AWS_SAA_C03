# Question 38

A Solutions Architect created a new Standard-class Amazon S3 bucket to store financial reports that are not frequently accessed but should immediately be available when an auditor requests the reports.

In S3 Standard - Infrequent Access storage class, which of the following statements are true? (Select TWO.)

## Options

A. It is designed for data that requires rapid access when needed.

B. It is designed for data that is accessed less frequently.

C. Ideal to use for data archiving.

D. It provides high latency and low throughput performance.

E. It automatically moves data to the most cost-effective access tier.

## Correct Answers

**A. It is designed for data that requires rapid access when needed.**

**B. It is designed for data that is accessed less frequently.**

## Explanation

Amazon S3 Standard-IA is for data accessed less frequently but requires rapid access when needed. It offers the same low latency and high throughput of S3 Standard with a low per GB storage price.

### Why other options are incorrect:

- **E** - This describes S3 Intelligent-Tiering.

- **D** - S3 provides low latency and high throughput.

- **C** - Data archiving uses S3 Glacier.

## References

- https://aws.amazon.com/s3/storage-classes/
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design High-Performing Architectures
