# Question 44

## Topic
Design Secure Architectures

## Question
A company runs a multi-tier web application in the AWS Cloud. The application tier is hosted on Amazon EC2 instances and the backend database is hosted on an Amazon Aurora for MySQL DB cluster. For security compliance, all of the application variables such as DB hostnames, environment settings, product keys, and database passwords must be stored securely with encryption.

Which of the following options is the most cost-effective solution to meet the requirements?

## Options
A. Store the values in a file saved in an Amazon S3 bucket. Enable encryption on the S3 bucket. Configure the application to download the file contents when it starts.

B. Store the values by creating secrets in AWS Secrets Manager. Use AWS KMS for the encryption. Use the BatchGetSecretValue API. Update the application to retrieve the values.

C. Store the values as key-value pairs in AWS Systems Manager OpsCenter. By default, the key-value pairs will be encrypted at rest. Configure the application to retrieve the variables when it starts.

D. Store the values by creating SecureString type parameters in AWS Systems Manager Parameter Store. Use AWS KMS for the encryption. Update the application to retrieve the parameter values.

## Correct Answer
D

## Explanation
AWS Systems Manager Parameter Store provides secure, hierarchical storage for configuration data and secrets management. You can store data such as passwords, database strings, and license codes as parameter values. You can store values as plain text or encrypted data.

Parameter Store is more cost-effective than Secrets Manager for storing static configuration values. Secrets Manager incurs approximately $0.40 per secret per month.

**Why other options are incorrect:**
- **Option A** is incorrect because downloading files from S3 on startup is not recommended for secrets.
- **Option B** is incorrect because Secrets Manager is more expensive for static values that don't require rotation.
- **Option C** is incorrect because OpsCenter is not meant as a datastore for key-value pairs.

## References
- https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter-store.html
- https://tutorialsdojo.com/aws-systems-manager/
