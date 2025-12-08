# Question 64

A company has 3 DevOps engineers that are handling its software development and infrastructure management processes. One of the engineers accidentally deleted a file hosted in Amazon S3 which has caused disruption of service.

What can the DevOps engineers do to prevent this from happening again?

## Options

A. Enable S3 Versioning and Multi-Factor Authentication Delete on the bucket.

B. Set up a signed URL for all users.

C. Use S3 Infrequently Accessed storage to store the data.

D. Create an IAM bucket policy that disables delete operation.

## Correct Answer

**A. Enable S3 Versioning and Multi-Factor Authentication Delete on the bucket.**

## Explanation

To avoid accidental deletion in Amazon S3:
- Enable Versioning - keeps multiple variants of an object
- Enable MFA Delete - requires additional authentication for permanent deletions

With MFA Delete enabled, it requires authentication for:
- Changing the versioning state of your bucket
- Permanently deleting an object version

### Why other options are incorrect:

- **C** - Changing storage class doesn't prevent accidental deletions.

- **B** - Signed URLs control access, not deletion prevention.

- **D** - Disabling delete entirely prevents legitimate deletions, not just accidental ones.

## References

- http://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html
- https://docs.aws.amazon.com/AmazonS3/latest/userguide/MultiFactorAuthenticationDelete.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Secure Architectures
