# Question 32

There was an incident in a production environment where user data stored in an Amazon S3 bucket was accidentally deleted by a Junior DevOps Engineer. The issue was escalated to management, and after a few days, an instruction was given to improve the security and protection of AWS resources.

What combination of the following options will protect the S3 objects in the bucket from both accidental deletion and overwriting? (Select TWO.)

## Options

A. Enable S3 Intelligent-Tiering

B. Disallow S3 Delete using an IAM bucket policy

C. Enable Multi-Factor Authentication Delete

D. Provide access to S3 data strictly through pre-signed URL only

E. Enable Versioning

## Correct Answers

**C. Enable Multi-Factor Authentication Delete**

**E. Enable Versioning**

## Explanation

By using Versioning and enabling MFA (Multi-Factor Authentication) Delete, you can secure and recover your S3 objects from accidental deletion or overwrite.

Versioning is a means of keeping multiple variants of an object in the same bucket. Versioning-enabled buckets enable you to recover objects from accidental deletion or overwrite. You can use versioning to preserve, retrieve, and restore every version of every object stored in your Amazon S3 bucket.

You can also optionally add another layer of security by configuring a bucket to enable MFA Delete, which requires additional authentication for either of the following operations:
- Change the versioning state of your bucket
- Permanently delete an object version

MFA Delete requires two forms of authentication together:
- Your security credentials
- The concatenation of a valid serial number, a space, and the six-digit code displayed on an approved authentication device

### Why other options are incorrect:

- **D** - Pre-signed URLs are useful when customers perform an object upload to your S3 bucket, but does not help in preventing accidental deletes.

- **B** - Disallowing S3 Delete using an IAM bucket policy will restrict all delete operations to your bucket. You still want users to be able to delete objects, just prevent accidental deletions.

- **A** - S3 intelligent tiering does not help prevent accidental deletion.

## References

- https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html
- https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Resilient Architectures
