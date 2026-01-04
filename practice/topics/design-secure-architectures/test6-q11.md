# Question 11

Web app migration from on-premises MySQL to AWS. Need SSL encryption and EC2 instance profile credentials for DB access.

Which solution is most suitable?

## Options

A. Aurora with Backtrack enabled.

B. RDS with IAM DB Authentication.

C. Use mysql client with --ssl-ca parameter.

D. RDS with encryption enabled.

## Correct Answer

**B. RDS with IAM DB Authentication.**

## Explanation

IAM DB Authentication:
- **SSL encryption**: Automatically enabled for connections
- **EC2 profile credentials**: Use IAM to authenticate, no password
- **Token-based**: 15-minute auth tokens
- **Centralized access**: Manage via IAM policies

### Why other options are incorrect:

- **A** - Backtrack rewinds DB, not for auth/encryption.

- **C** - Still requires password-based auth.

- **D** - Encryption at rest, not connection auth.

## References

- https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAMDBAuth.html
- https://tutorialsdojo.com/amazon-relational-database-service-amazon-rds/

## Domain

Design Secure Architectures
