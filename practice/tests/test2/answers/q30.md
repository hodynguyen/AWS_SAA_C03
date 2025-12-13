# Question 30

A Solutions Architect is building a cloud infrastructure where Amazon EC2 instances require access to various AWS services, such as Amazon S3 and Amazon Redshift. The Architect will also need to provide access to system administrators so that the administrators can deploy and test changes.

Which configuration should be used to ensure that access to the resources is secured and not compromised? (Select TWO.)

## Options

A. Assign an IAM user for each EC2 Instance.

B. Store the AWS Access Keys in the EC2 instance.

C. Store the AWS Access Keys in ACM.

D. Enable Multi-Factor Authentication.

E. Assign an IAM role to the EC2 instance.

## Correct Answers

**D. Enable Multi-Factor Authentication.**

**E. Assign an IAM role to the EC2 instance.**

## Explanation

Always associate IAM roles with EC2 instances (not IAM users) for accessing other AWS services. IAM roles provide temporary credentials that are automatically rotated.

AWS Multi-Factor Authentication (MFA) adds an extra layer of protection on top of username and password.

### Why other options are incorrect:

- **B** - Storing access keys in EC2 can be compromised.

- **A** - IAM users are less flexible than IAM roles for EC2.

- **C** - ACM is for SSL/TLS certificates, not access keys.

## References

- https://aws.amazon.com/iam/details/mfa/
- https://tutorialsdojo.com/aws-identity-and-access-management-iam/

## Domain

Design Secure Architectures
