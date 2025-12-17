# Question 10

## Topic
Design Secure Architectures

## Question
A company is generating confidential data that is saved on its on-premises data center. As a backup solution, the company wants to upload its data to an Amazon S3 bucket. In compliance with its internal security mandate, the encryption of the data must be done before sending it to S3. The company must spend time managing and rotating the encryption keys as well as controlling who can access those keys.

Which of the following methods can achieve this requirement? (Select TWO.)

## Options
A. Set up Client-Side Encryption with S3 managed encryption keys.

B. Set up Server-Side Encryption (SSE) with Amazon EC2 key pair.

C. Set up Server-Side Encryption with keys stored in a separate S3 bucket.

D. Set up Client-Side Encryption using a client-side master key.

E. Set up Client-Side Encryption with AWS KMS key.

## Correct Answers
**D. Set up Client-Side Encryption using a client-side master key.**

**E. Set up Client-Side Encryption with AWS KMS key.**

## Explanation
Data protection refers to protecting data while in transit and at rest. You can protect data in transit by using SSL or by using client-side encryption.

For Client-Side Encryption, you can encrypt data client-side and upload the encrypted data to Amazon S3. In this case, you manage the encryption process, the encryption keys, and related tools.

Options for client-side encryption:
- Use Client-Side Encryption with AWS KMS key
- Use Client-Side Encryption Using a Client-Side Master Key

**Why other options are incorrect:**
- **Option A** is incorrect because you can't have an Amazon S3 managed encryption key for client-side encryption.
- **Option B** is incorrect because you can't use an EC2 key pair for encrypting S3 data.
- **Option C** is incorrect because storing encryption keys in S3 is a security risk and not recommended.

## References
- http://docs.aws.amazon.com/AmazonS3/latest/dev/UsingEncryption.html
- https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingClientSideEncryption.html
- https://tutorialsdojo.com/amazon-s3/
