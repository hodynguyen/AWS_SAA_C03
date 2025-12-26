# Question 33

## Topic
Design Cost-Optimized Architectures

## Question
A company is looking to store its confidential financial files in AWS, which are accessed every week. The Architect was instructed to set up the storage system, which uses envelope encryption and automates key rotation. It should also provide an audit trail that shows who used the encryption key and by whom for security purposes.

Which combination of actions should the Architect implement to satisfy the requirement in the most cost-effective way? (Select TWO.)

## Options
A. Configure Server-Side Encryption with Amazon S3-Managed Keys (SSE-S3).

B. Configure Server-Side Encryption with AWS KMS Keys (SSE-KMS).

C. Use Amazon S3 Glacier Deep Archive to store the data.

D. Use Amazon S3 to store the data.

E. Configure Server-Side Encryption with Customer-Provided Keys (SSE-C).

## Correct Answer
B, D

## Explanation
Server-side encryption is the encryption of data at its destination by the application or service that receives it. AWS Key Management Service (AWS KMS) is a service that combines secure, highly available hardware and software to provide a key management system scaled for the cloud. Amazon S3 uses AWS KMS keys to encrypt your Amazon S3 objects. SSE-KMS encrypts only the object data. Any object metadata is not encrypted. If you use KMS keys, you use AWS KMS via the AWS Management Console or AWS KMS APIs to centrally create encryption keys, define the policies that control how keys can be used, and audit key usage to prove that they are being used correctly. You can use these keys to protect your data in Amazon S3 buckets.

A KMS key is a logical representation of a cryptographic key. The KMS key includes metadata, such as the key ID, creation date, description, and key state. The KMS key also contains the key material used to encrypt and decrypt data. You can use a KMS key to encrypt and decrypt up to 4 KB (4096 bytes) of data. Typically, you use KMS keys to generate, encrypt, and decrypt the data keys that you use outside of AWS KMS to encrypt your data. This strategy is known as envelope encryption.

You have three mutually exclusive options depending on how you choose to manage the encryption keys:

Use Server-Side Encryption with Amazon S3-Managed Keys (SSE-S3) – Each object is encrypted with a unique key. As an additional safeguard, it encrypts the key itself with a master key that it regularly rotates. Amazon S3 server-side encryption uses one of the strongest block ciphers available, 256-bit Advanced Encryption Standard (AES-256), to encrypt your data.

Use Server-Side Encryption with KMS Key Stored in AWS Key Management Service (SSE-KMS) – Similar to SSE-S3, but with some additional benefits and charges for using this service. There are separate permissions for the use of a KMS key that provides added protection against unauthorized access of your objects in Amazon S3. SSE-KMS also provides you with an audit trail that shows when your KMS key was used and by whom. Additionally, you can create and manage customer-managed key or use AWS managed KMS keys that are unique to you, your service, and your Region.

Use Server-Side Encryption with Customer-Provided Keys (SSE-C) – You manage the encryption keys and Amazon S3 manages the encryption, as it writes to disks, and decryption when you access your objects.

In the scenario, the company needs to store financial files in AWS which are accessed every week and the solution should use envelope encryption. This requirement can be fulfilled by using an Amazon S3 configured with Server-Side Encryption with AWS KMS keys (SSE-KMS).

Hence, the correct answers are:

- Use Amazon S3 to store the data.

- Configure Server-Side Encryption with AWS KMS Keys (SSE-KMS).

References:

https://docs.aws.amazon.com/AmazonS3/latest/dev/serv-side-encryption.html

https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingKMSEncryption.html

https://docs.aws.amazon.com/kms/latest/developerguide/services-s3.html

Check out this Amazon S3 Cheat Sheet:

https://tutorialsdojo.com/amazon-s3/

**Why other options are incorrect:**

- The option that says: Use Amazon S3 Glacier Deep Archive to store the data is incorrect. Although this primarily provides the most cost-effective storage solution, it is not the appropriate service to use if the files being stored are frequently accessed every week.

- The option that says: Configure Server-Side Encryption with Customer-Provided Keys (SSE-C) is incorrect. Although you can typically configure automatic key rotation, it does not provide an audit trail showing when your KMS Key was used and by whom, unlike Server-Side Encryption with AWS KMS Keys (SSE-KMS).

- The option that says: Configure Server-Side Encryption with Amazon S3-Managed Keys (SSE-S3) is incorrect. Just like the previous option, it does not provide an audit log detailing key usage. Unlike Server-Side Encryption with AWS KMS Keys (SSE-KMS), SSE-S3 does not allow tracking of encryption and decryption events through AWS CloudTrail.

