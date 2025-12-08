# Question 61

A financial application consists of an Auto Scaling group of Amazon EC2 instances, an Application Load Balancer, and a MySQL RDS instance set up in a Multi-AZ Deployment configuration. To protect customers' confidential data, it must be ensured that the Amazon RDS database is only accessible using an authentication token specific to the profile credentials of EC2 instances.

Which of the following actions should be taken to meet this requirement?

## Options

A. Use a combination of IAM and STS to enforce restricted access to your RDS instance using a temporary authentication token.

B. Enable the IAM DB Authentication.

C. Configure SSL in your application to encrypt the database connection to RDS.

D. Create an IAM Role and assign it to your EC2 instances which will grant exclusive access to your RDS instance.

## Correct Answer

**B. Enable the IAM DB Authentication.**

## Explanation

IAM database authentication works with MySQL and PostgreSQL. With this authentication method, you don't need to use a password when you connect to a DB instance. Instead, you use an authentication token.

Benefits:
- Network traffic is encrypted using SSL
- You can use IAM to centrally manage database access
- For EC2, you can use profile credentials instead of a password

### Why other options are incorrect:

- **C** - SSL encrypts traffic but doesn't provide token-based authentication.

- **D** - IAM Roles alone don't provide database authentication without IAM DB Authentication.

- **A** - STS is not directly compatible with RDS authentication in this way.

## References

- https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAMDBAuth.html
- https://aws.amazon.com/rds/
- https://tutorialsdojo.com/amazon-relational-database-service-amazon-rds/

## Domain

Design Secure Architectures
