# Question 23

## Topic
Design Secure Architectures

## Question
A Solutions Architect is working for a large insurance firm. To maintain compliance with HIPAA laws, all data that is backed up or stored on Amazon S3 needs to be encrypted at rest.

Which encryption methods can be employed, assuming S3 is being used for storing financial-related data? (Select TWO.)

## Options
A. Store the data in encrypted EBS snapshots

B. Store the data on EBS volumes with encryption enabled instead of using Amazon S3

C. Use AWS Shield to protect your data at rest

D. Enable SSE on an S3 bucket to make use of AES-256 encryption

E. Encrypt the data using your own encryption keys then copy the data to Amazon S3 over HTTPS endpoints.

## Correct Answers
**D. Enable SSE on an S3 bucket to make use of AES-256 encryption**

**E. Encrypt the data using your own encryption keys then copy the data to Amazon S3 over HTTPS endpoints.**

## Explanation
Data protection refers to protecting data while in transit and at rest. You can protect data in transit by using SSL or by using client-side encryption. For data at rest in Amazon S3:

- Use Server-Side Encryption (SSE) – Amazon S3 encrypts your object before saving it on disks and decrypts it when you download.
- Use Client-Side Encryption – You can encrypt data client-side and upload the encrypted data to Amazon S3.

**Why other options are incorrect:**
- **Options A and B** are incorrect because these options are for protecting data in EBS volumes, not S3.
- **Option C** is incorrect because AWS Shield protects against DDoS attacks, not for data encryption at rest.

## References
- https://docs.aws.amazon.com/AmazonS3/latest/dev/serv-side-encryption.html
- https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingClientSideEncryption.html
- https://tutorialsdojo.com/amazon-s3/
