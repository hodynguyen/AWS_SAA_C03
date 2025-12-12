# Question 18

An organization needs to control access to several Amazon S3 buckets. The organization plans to use a gateway endpoint to allow access to trusted buckets.

Which of the following could help you achieve this requirement?

## Options

A. Generate a bucket policy for trusted VPCs.

B. Generate a bucket policy for trusted S3 buckets.

C. Generate an endpoint policy for trusted VPCs.

D. Generate an endpoint policy for trusted S3 buckets.

## Correct Answer

**D. Generate an endpoint policy for trusted S3 buckets.**

## Explanation

A Gateway endpoint is a type of VPC endpoint that provides reliable connectivity to Amazon S3 and DynamoDB without requiring an internet gateway.

When you create a Gateway endpoint, you can attach an endpoint policy that controls access to the service. Using an endpoint policy to allow traffic to trusted S3 buckets is more efficient than configuring individual bucket policies.

### Why other options are incorrect:

- **B** - Bucket policies work but require configuration for each bucket.

- **A, C** - These allow access to VPCs, not trusted S3 buckets.

## References

- https://docs.aws.amazon.com/vpc/latest/userguide/vpc-endpoints-s3.html
- https://tutorialsdojo.com/amazon-vpc/

## Domain

Design Secure Architectures
