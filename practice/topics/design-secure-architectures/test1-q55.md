# Question 55

An online medical system hosted in AWS stores sensitive Personally Identifiable Information (PII) of the users in an Amazon S3 bucket. Both the master keys and the unencrypted data should never be sent to AWS to comply with the strict compliance and regulatory requirements of the company.

Which S3 encryption technique should the Architect use?

## Options

A. Use S3 client-side encryption with a client-side master key.

B. Use S3 client-side encryption with an AWS KMS key.

C. Use S3 server-side encryption with customer provided key.

D. Use S3 server-side encryption with an AWS KMS key.

## Correct Answer

**A. Use S3 client-side encryption with a client-side master key.**

## Explanation

When using client-side master key for client-side encryption, your master keys and unencrypted data are never sent to AWS.

How it works:
1. The client generates a data encryption key locally
2. The client encrypts the data using the data key
3. The client encrypts the data key using your master key
4. The client uploads the encrypted data and encrypted data key to S3

### Why other options are incorrect:

- **B** - With KMS key, you provide a KeyId to AWS, meaning the master key reference is sent to AWS.

- **C & D** - Server-side encryption means unencrypted data is sent to AWS for encryption.

## References

- https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingClientSideEncryption.html
- https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingEncryption.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Secure Architectures
