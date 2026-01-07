# Question 63

Multiple sandbox accounts. Access main account S3. Monitor for PII/financial data. Lowest cost, least effort.

## Options

A. Pre-signed URLs + Storage Lens.

B. IAM policy per user + Detective.

C. S3 bucket policy + Macie.

D. Cross-account replication + Audit Manager.

## Correct Answer

**C. S3 bucket policy + Macie.**

## Explanation

Cross-account S3 access + PII detection:
- **Bucket policy**: Grant access from other accounts
- **Amazon Macie**: ML for PII/sensitive data
- **Single location**: Manage from bucket
- **Cost-effective**: No data replication

### Why other options are incorrect:

- **A** - Pre-signed URLs expire; Storage Lens doesn't detect PII.

- **B** - IAM policy per user is high overhead; Detective doesn't detect PII.

- **D** - Replication adds cost; Audit Manager doesn't detect PII.

## References

- https://aws.amazon.com/premiumsupport/knowledge-center/cross-account-access-s3/
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Cost-Optimized Architectures
