# Question 47

A company requires all the data stored in the cloud to be encrypted at rest. To easily integrate this with other AWS services, they must have full control over the encryption of the created keys and also the ability to immediately remove the key material from AWS KMS. The solution should also be able to audit the key usage independently of AWS CloudTrail.

Which of the following options will meet this requirement?

## Options

A. Use AWS Key Management Service to create AWS owned Keys and store the non-extractable key material in AWS CloudHSM.

B. Use AWS Key Management Service to create AWS managed keys and store the non-extractable key material in AWS CloudHSM.

C. Use AWS Key Management Service to create a KMS key in a custom key store and store the non-extractable key material in AWS CloudHSM.

D. Use AWS Key Management Service to create a KMS key in a custom key store and store the non-extractable key material in Amazon S3.

## Correct Answer

**C. Use AWS Key Management Service to create a KMS key in a custom key store and store the non-extractable key material in AWS CloudHSM.**

## Explanation

The AWS KMS custom key store feature combines controls provided by AWS CloudHSM with the integration and ease of use of AWS KMS. When you create keys in AWS KMS, you can choose to generate the key material in your CloudHSM cluster.

Custom key stores are useful when:
- You need key material safeguarded in a dedicated HSM under your direct control
- You require the capability to promptly remove key material from AWS KMS
- Your compliance obligations mandate independent auditing beyond CloudTrail

### Why other options are incorrect:

- **D** - Amazon S3 is for general storage, not for cryptographic key management.

- **A & B** - AWS owned and managed keys are managed by AWS and don't allow independent auditing outside CloudTrail.

## References

- https://docs.aws.amazon.com/kms/latest/developerguide/custom-key-store-overview.html
- https://docs.aws.amazon.com/kms/latest/developerguide/keystore-cloudhsm.html
- https://tutorialsdojo.com/aws-key-management-service-aws-kms/

## Domain

Design Secure Architectures
