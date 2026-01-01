# Question 53

EBS volumes must be encrypted for HIPAA compliance.

What does AWS use to secure EBS data at rest? (Select TWO.)

## Options

A. S3 Server-Side Encryption.

B. Your own keys in KMS.

C. Amazon-managed keys in KMS.

D. SSL certificates from ACM.

E. Password in CloudHSM.

F. S3 Client-Side Encryption.

## Correct Answer

**B. Your own keys in KMS.**

**C. Amazon-managed keys in KMS.**

## Explanation

EBS encryption uses KMS:
- **AWS-managed keys**: Default encryption key
- **Customer-managed keys**: Your own CMK in KMS
- **AES-256**: Encryption algorithm
- **Seamless**: No application changes needed

### Why other options are incorrect:

- **A, F** - S3 encryption is for S3, not EBS.

- **D** - ACM certificates are for TLS/SSL, not storage encryption.

- **E** - CloudHSM stores keys, not passwords.

## References

- https://aws.amazon.com/ebs/faqs/
- https://tutorialsdojo.com/amazon-ebs/

## Domain

Design Secure Architectures
