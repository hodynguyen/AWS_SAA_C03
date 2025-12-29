# Question 35

A client has reproducible but confidential files. Files are accessed frequently for the first month, then rarely. Files with `tdojo-finance` prefix need millisecond retrieval; others have no time requirement.

What is the most cost-effective storage solution?

## Options

A. Store in S3, then use Intelligent-Tiering via lifecycle policy.

B. Store in S3, then move tdojo-finance prefix to S3-IA, others to Glacier.

C. Store in S3, then move entire bucket to S3-IA.

D. Store in S3, then move tdojo-finance prefix to One Zone-IA, others to Glacier.

## Correct Answer

**D. Store in S3, then move tdojo-finance prefix to One Zone-IA, others to Glacier.**

## Explanation

S3 Lifecycle Policies can filter by prefix:
- **tdojo-finance → One Zone-IA**: Millisecond retrieval, lowest IA cost (files are reproducible, so single-AZ is acceptable)
- **Others → Glacier**: Lowest storage cost for rarely accessed data

### Why other options are incorrect:

- **A** - Intelligent-Tiering has monitoring fees and delays before moving data. If you know access patterns, use explicit policies.

- **B** - S3-IA costs more than One Zone-IA. Since files are reproducible, single-AZ is acceptable.

- **C** - Moving everything to S3-IA doesn't optimize for rarely accessed files that should go to Glacier.

## References

- https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Cost-Optimized Architectures
