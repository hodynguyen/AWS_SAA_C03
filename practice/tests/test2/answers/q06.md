# Question 6

An application is hosted in AWS Fargate and uses RDS database in Multi-AZ Deployments configuration with several Read Replicas. A Solutions Architect was instructed to ensure that all of their database credentials, API keys, and other secrets are encrypted and rotated on a regular basis to improve data security.

Which of the following is the MOST appropriate solution to secure the credentials?

## Options

A. Store the database credentials, API keys, and other secrets to AWS ACM.

B. Store the database credentials, API keys, and other secrets in AWS KMS.

C. Use AWS Secrets Manager to store and encrypt the database credentials, API keys, and other secrets. Enable automatic rotation for all of the credentials.

D. Store the database credentials, API keys, and other secrets to Systems Manager Parameter Store each with a SecureString data type. The credentials are automatically rotated by default.

## Correct Answer

**C. Use AWS Secrets Manager to store and encrypt the database credentials, API keys, and other secrets. Enable automatic rotation for all of the credentials.**

## Explanation

AWS Secrets Manager helps you manage secrets like database credentials, passwords, and API keys. It enables you to replace hardcoded credentials with an API call.

Key features:
- Store and control access to secrets centrally
- Automatic rotation according to schedule
- Replace long-term secrets with short-term ones

### Why other options are incorrect:

- **D** - Parameter Store doesn't rotate credentials by default.

- **A** - ACM is for SSL/TLS certificates, not credentials.

- **B** - KMS is for encryption keys, not storing secrets.

## References

- https://aws.amazon.com/secrets-manager/
- https://tutorialsdojo.com/aws-secrets-manager/

## Domain

Design Secure Architectures
