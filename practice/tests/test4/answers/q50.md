# Question 50

A bank needs to ensure S3 objects are encrypted with AES-256. The encryption key must automatically rotate yearly.

Which solution has the least operational overhead?

## Options

A. Create SCP requiring AES256 header. Enable SSE-S3. Modify built-in key rotation to yearly.

B. Create S3 bucket policy denying uploads without AES256 header. Enable SSE-S3. Use built-in key rotation.

C. Create bucket policy requiring aws:kms header. Enable S3 Object Lock in compliance mode.

D. Create customer-managed KMS key. Configure as default encryption. Manually rotate yearly.

## Correct Answer

**B. Create S3 bucket policy denying uploads without AES256 header. Enable SSE-S3. Use built-in key rotation.**

## Explanation

SSE-S3 (S3-managed keys):
- **AES-256 encryption**: Uses 256-bit Advanced Encryption Standard
- **Automatic key rotation**: AWS rotates keys automatically (you cannot change the schedule)
- **Bucket policy enforcement**: Deny uploads missing `x-amz-server-side-encryption: AES256`

### Why other options are incorrect:

- **A** - You cannot modify SSE-S3 rotation schedule. SCPs are for organization-level controls, not S3 buckets.

- **C** - SSE-KMS doesn't use AES-256. Object Lock is for WORM, not encryption.

- **D** - Manual rotation adds operational overhead.

## References

- https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingServerSideEncryption.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Secure Architectures
