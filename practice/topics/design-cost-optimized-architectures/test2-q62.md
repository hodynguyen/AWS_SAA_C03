# Question 62

A company has a requirement to retain application logs for 7 years for compliance purposes. The logs should be easily searchable for the first 90 days and archived afterward.

Which solution meets these requirements cost-effectively?

## Options

A. Store logs in Amazon CloudWatch Logs with a 7-year retention period.

B. Store logs in Amazon S3 Standard and use S3 lifecycle policies to transition to S3 Glacier after 90 days.

C. Store logs in Amazon EBS volumes with snapshots.

D. Store logs in Amazon DynamoDB with TTL enabled.

## Correct Answer

**B. Store logs in Amazon S3 Standard and use S3 lifecycle policies to transition to S3 Glacier after 90 days.**

## Explanation

S3 Standard provides searchability for the first 90 days. Lifecycle policies automatically transition objects to S3 Glacier for low-cost archival storage for the remaining period.

### Why other options are incorrect:

- **A** - CloudWatch Logs is expensive for long-term retention.

- **C** - EBS snapshots are not cost-effective for logs.

- **D** - TTL would delete data, not archive it.

## References

- https://docs.aws.amazon.com/AmazonS3/latest/userguide/lifecycle-transition-general-considerations.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Cost-Optimized Architectures
