# Question 50

## Topic
Design Secure Architectures

## Question
A multinational bank is storing its confidential files in an S3 bucket. The security team recently performed an audit, and the report shows that multiple files have been uploaded without 256-bit Advanced Encryption Standard (AES) server-side encryption. For added protection, the encryption key must be automatically rotated every year. The solutions architect must ensure that there would be no other unencrypted files uploaded in the S3 bucket in the future.

Which of the following will meet these requirements with the LEAST operational overhead?

## Options
A. Create a Service Control Policy (SCP) for the S3 bucket that rejects any object uploads unless the request includes the s3:x-amz-server-side-encryption": "AES256" header. Enable server-side encryption with Amazon S3-managed encryption keys (SSE-S3) and modify the built-in key rotation feature of the SSE-S3 encryption keys to rotate the key yearly.

B. Create an S3 bucket policy that denies permissions to upload an object unless the request includes the s3:x-amz-server-side-encryption": "AES256" header. Enable server-side encryption with Amazon S3-managed encryption keys (SSE-S3) and rely on the built-in key rotation feature of the SSE-S3 encryption keys.

C. Create an S3 bucket policy for the S3 bucket that rejects any object uploads unless the request includes the s3:x-amz-server-side-encryption":"aws:kms" header. Enable the S3 Object Lock in compliance mode for all objects to automatically rotate the built-in AES256 customer-managed key of the bucket.

D. Create a new customer-managed key from the AWS Key Management Service (AWS KMS). Configure the default encryption behavior of the bucket to use the customer-managed key. Manually rotate the KMS key and every year.

## Correct Answer
B

## Explanation
A bucket policy is a resource-based policy that you can use to grant access permissions to your bucket and the objects in it. Server-side encryption protects data at rest. Amazon S3 encrypts each object with a unique key. Amazon S3 server-side encryption uses one of the strongest block ciphers available to encrypt your data, 256-bit Advanced Encryption Standard (AES-256).

If you need server-side encryption for all of the objects that are stored in a bucket, use a bucket policy. You can create a bucket policy that denies permissions to upload an object unless the request includes the x-amz-server-side-encryption header to request server-side encryption.

Automatic key rotation is disabled by default on customer managed keys but authorized users can enable and disable it. When you enable (or re-enable) automatic key rotation, AWS KMS automatically rotates the KMS key one year (approximately 365 days) after the enable date and every year thereafter.

AWS KMS automatically rotates AWS managed keys every year (approximately 365 days). You cannot enable or disable key rotation for AWS managed keys.

Hence, the correct answer is Create an S3 bucket policy that denies permissions to upload an object unless the request includes the s3:x-amz-server-side-encryption": "AES256" header. Enable server-side encryption with Amazon S3-managed encryption keys (SSE-S3) and rely on the built-in key rotation feature of the SSE-S3 encryption keys.

References:

https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucket-policies.html

https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingServerSideEncryption.html

https://docs.aws.amazon.com/kms/latest/developerguide/rotate-keys.html

Check out this Amazon S3 Cheat Sheet:

https://tutorialsdojo.com/amazon-s3/

**Why other options are incorrect:**

- The option that says: Create a Service Control Policy (SCP) for the S3 bucket that rejects any object uploads unless the request includes the s3:x-amz-server-side-encryption": "AES256" header. Enable server-side encryption with Amazon S3-managed encryption keys (SSE-S3) and modify the built-in key rotation feature of the SSE-S3 encryption keys to rotate the key yearly is incorrect. Although it could work, you cannot modify the built-in key rotation feature manually in SSE-S3. These keys are managed by AWS, and not you. Moreover, you have to use a bucket policy in Amazon S3 and not a Service Control Policy, since the latter is primarily used for controlling multiple AWS accounts.

- The option that says: Create a new customer-managed key from the AWS Key Management Service (AWS KMS). Configure the default encryption behavior of the bucket to use the customer-managed key. Manually rotate the KMS key and every year is incorrect because this solution is missing a bucket policy that denies S3 object uploads without any encryption. Conversely, the act of manually rotating the KMS key each and every year adds to the manual management overhead for this solution.

- The option that says: Create an S3 bucket policy for the S3 bucket that rejects any object uploads unless the request includes the s3:x-amz-server-side-encryption":"aws:kms" header. Enable the S3 Object Lock in compliance mode for all objects to automatically rotate the built-in AES256 customer-managed key of the bucket is incorrect because the scenario says that the encryption required is 256-bit Advanced Encryption Standard (AES-256), not AWS Key Management Service (SSE-KMS). Take note that that if the value of the s3:x-amz-server-side-encryption header is aws:kms, then the S3 encryption type is SSE-KMS. This type of server-side encryption does not use a 256-bit Advanced Encryption Standard (AES-256), unlike the SSE-S3 type. In addition, an S3 Object Lock feature is not used for encryption but instead, for preventing the objects from being deleted or overwritten for a fixed amount of time or indefinitely.

