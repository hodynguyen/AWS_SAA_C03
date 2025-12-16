# Question 55

A company wants to encrypt all data stored in Amazon S3 using keys that it manages itself. The company must retain full control over the encryption keys.

Which solution meets this requirement?

## Options

A. Use SSE-S3 with Amazon S3 managed keys.

B. Use SSE-KMS with AWS managed keys.

C. Use SSE-C with customer-provided keys.

D. Use SSE-KMS with customer managed keys (CMK).

## Correct Answer

**D. Use SSE-KMS with customer managed keys (CMK).**

## Explanation

SSE-KMS with customer managed CMKs provides full control over the encryption keys while leveraging AWS KMS for key management. You can define key policies and audit key usage.

### Why other options are incorrect:

- **A** - SSE-S3 uses Amazon managed keys.

- **B** - AWS managed keys are not customer-controlled.

- **C** - SSE-C requires managing keys outside AWS.

## References

- https://docs.aws.amazon.com/AmazonS3/latest/userguide/serv-side-encryption.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Secure Architectures
