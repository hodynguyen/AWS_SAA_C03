# Question 52

A company has strict data sovereignty requirements and must ensure that data does not leave a specific AWS Region. The company uses Amazon S3 for data storage.

Which feature should be used to enforce this requirement?

## Options

A. Enable S3 Object Lock.

B. Configure S3 Bucket Policies with IP restrictions.

C. Enable S3 Block Public Access.

D. Create an S3 Bucket that is restricted to a specific AWS Region using bucket policy conditions.

## Correct Answer

**D. Create an S3 Bucket that is restricted to a specific AWS Region using bucket policy conditions.**

## Explanation

S3 buckets are regional by design. To enforce data sovereignty, use bucket policies with `aws:RequestedRegion` condition to ensure operations occur only within the specified region.

### Why other options are incorrect:

- **A** - Object Lock is for preventing deletions.

- **B** - IP restrictions don't address data residency.

- **C** - Block Public Access prevents public exposure.

## References

- https://docs.aws.amazon.com/AmazonS3/latest/userguide/using-iam-policies.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Secure Architectures
