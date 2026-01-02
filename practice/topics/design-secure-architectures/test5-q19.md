# Question 19

Multiple applications need secure access to RDS MySQL. Each IAM user must use short-lived authentication tokens.

Which solution is most suitable?

## Options

A. Use IAM DB Authentication with AWSAuthenticationPlugin.

B. Use AWS Secrets Manager for short-lived tokens.

C. Use AWS IAM Identity Center to access RDS.

D. Use MFA token to connect to database.

## Correct Answer

**A. Use IAM DB Authentication with AWSAuthenticationPlugin.**

## Explanation

IAM DB Authentication:
- **15-minute tokens**: Short-lived authentication
- **No passwords**: Uses IAM credentials instead
- **SSL encrypted**: Network traffic protected
- **AWSAuthenticationPlugin**: MySQL plugin for IAM auth

### Why other options are incorrect:

- **B** - Secrets Manager stores secrets, doesn't generate DB auth tokens.

- **C** - IAM Identity Center is for AWS account access, not RDS.

- **D** - MFA is for AWS console, not database connections.

## References

- https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAMDBAuth.html
- https://tutorialsdojo.com/amazon-rds/

## Domain

Design Secure Architectures
