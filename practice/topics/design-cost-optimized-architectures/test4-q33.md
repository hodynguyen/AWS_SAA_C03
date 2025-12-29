# Question 33

A company needs to store confidential financial files accessed weekly. Requirements: envelope encryption, automatic key rotation, and audit trail showing key usage.

Which solutions satisfy these requirements cost-effectively? (Select TWO.)

## Options

A. Configure SSE-S3 (S3-Managed Keys).

B. Configure SSE-KMS (AWS KMS Keys).

C. Use S3 Glacier Deep Archive.

D. Use Amazon S3.

E. Configure SSE-C (Customer-Provided Keys).

## Correct Answer

**B. Configure SSE-KMS (AWS KMS Keys).**

**D. Use Amazon S3.**

## Explanation

SSE-KMS provides:
- **Envelope encryption**: Data key encrypts data, KMS key encrypts data key
- **Automatic key rotation**: Enable yearly rotation for customer-managed keys
- **Audit trail**: CloudTrail logs all key usage (who, when, what)

S3 Standard is appropriate for weekly access patterns.

### Why other options are incorrect:

- **A** - SSE-S3 doesn't provide audit trail or user-controlled key rotation.

- **C** - Glacier Deep Archive has long retrieval times, not suitable for weekly access.

- **E** - SSE-C requires you to manage keys and doesn't provide AWS audit trail.

## References

- https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingKMSEncryption.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Cost-Optimized Architectures
