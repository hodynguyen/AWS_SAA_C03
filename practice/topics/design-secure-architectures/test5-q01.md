# Question 1

A company troubleshoots operational issues by logging AWS API call history. The solution must identify recent changes (creation, modification, deletion) and encrypt the log files.

Which approach implements the encryption?

## Options

A. Use CloudTrail and configure the destination Glacier archive to use SSE.

B. Use CloudTrail and configure the destination S3 bucket to use SSE.

C. Use CloudTrail and configure SSE with AES-128 encryption.

D. Use CloudTrail with its default settings.

## Correct Answer

**D. Use CloudTrail with its default settings.**

## Explanation

CloudTrail encrypts log files by default:
- **SSE-S3**: Automatic server-side encryption with AES-256
- **S3 storage**: Logs stored in S3

No additional configuration needed—encryption is enabled out of the box.

### Why other options are incorrect:

- **A** - CloudTrail stores logs in S3, not Glacier directly.

- **B** - Already encrypted by default, no need to configure manually.

- **C** - SSE-S3 uses AES-256, not AES-128.

## References

- https://docs.aws.amazon.com/awscloudtrail/latest/userguide/how-cloudtrail-works.html
- https://tutorialsdojo.com/aws-cloudtrail/

## Domain

Design Secure Architectures
