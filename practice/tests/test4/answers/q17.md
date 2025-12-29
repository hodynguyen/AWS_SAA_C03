# Question 17

A media company stores high-quality videos in S3 Standard. Videos are frequently accessed only during the first three months after posting.

How should the company automatically transfer data from S3 to Glacier?

## Options

A. Use Lifecycle Policies

B. Use Amazon SWF

C. Use a custom shell script that transfers data from S3 to Glacier

D. Use Amazon SQS

## Correct Answer

**A. Use Lifecycle Policies**

## Explanation

S3 Lifecycle Policies automate the transition of objects between storage classes. You can configure rules to:
- **Transition actions**: Move objects to S3-IA after 30 days, then to Glacier after 90 days
- **Expiration actions**: Delete objects after a specified period

This is the native, zero-code solution for automated storage tiering.

### Why other options are incorrect:

- **B** - SWF is a workflow coordination service, not for S3 data management.

- **C** - Custom scripts require maintenance and are error-prone compared to native Lifecycle Policies.

- **D** - SQS is a message queue service, not for data archival.

## References

- https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Cost-Optimized Architectures
