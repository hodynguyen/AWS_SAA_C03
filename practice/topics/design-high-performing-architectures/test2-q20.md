# Question 20

A company has a serverless application made up of AWS Amplify, Amazon API Gateway and a Lambda function. The application is connected to an Amazon RDS MySQL database inside a private subnet. There are times during peak loads when the database throws a "too many connections" error.

Which solution could the company take to resolve the issue?

## Options

A. Increase the rate limit of API Gateway

B. Increase the concurrency limit of the Lambda function

C. Provision an RDS Proxy between the Lambda function and RDS database instance

D. Increase the memory allocation of the Lambda function

## Correct Answer

**C. Provision an RDS Proxy between the Lambda function and RDS database instance**

## Explanation

RDS Proxy helps you manage a large number of connections from Lambda to an RDS database by establishing a warm connection pool to the database. Your Lambda functions interact with RDS Proxy instead of your database instance.

This allows your Lambda applications to reuse existing connections, rather than creating new connections for every function invocation.

### Why other options are incorrect:

- **B** - More concurrency = more connections = worse problem.

- **A** - Rate limiting doesn't fix database connections.

- **D** - Memory doesn't affect connection pooling.

## References

- https://aws.amazon.com/rds/proxy/
- https://tutorialsdojo.com/amazon-relational-database-service-amazon-rds/

## Domain

Design High-Performing Architectures
