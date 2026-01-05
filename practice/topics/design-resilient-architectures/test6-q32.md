# Question 32

Cross-Region Replication disabled on S3 bucket. Why?

## Options

A. CRR only for S3-IA.

B. Premium feature for Enterprise.

C. Need to enable versioning first.

D. CRR only for S3 One Zone-IA.

## Correct Answer

**C. Need to enable versioning first.**

## Explanation

S3 Cross-Region Replication:
- **Versioning required**: Both source and destination
- **Different regions**: Source and destination
- **IAM permissions**: S3 needs permission to replicate
- **All storage classes**: Works with any S3 class

### Why other options are incorrect:

- **A, D** - CRR works with all storage classes.

- **B** - Available to all support plans, not premium.

## References

- https://docs.aws.amazon.com/AmazonS3/latest/dev/crr.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Resilient Architectures
