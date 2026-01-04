# Question 12

New IAM user created via CLI needs to make API calls to S3, DynamoDB, Lambda.

What must be done?

## Options

A. Enable Multi-Factor Authentication.

B. User is already capable of API calls.

C. Assign an IAM Policy.

D. Create Access Keys and attach permissions.

## Correct Answer

**D. Create Access Keys and attach permissions.**

## Explanation

IAM user API access:
- **Access Keys**: Required for CLI/API access
- **CLI-created users**: No credentials by default
- **Secret Access Key**: Only shown once at creation
- **Permissions**: Still need IAM policies

### Why other options are incorrect:

- **A** - MFA adds security, doesn't provide credentials.

- **B** - CLI-created users have no credentials by default.

- **C** - Policy alone doesn't provide access keys.

## References

- https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html
- https://tutorialsdojo.com/aws-identity-and-access-management-iam/

## Domain

Design Secure Architectures
