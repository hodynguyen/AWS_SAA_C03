# Question 61

A company runs a serverless application using AWS Lambda functions. The functions retrieve configuration data from a database. The company wants to reduce latency and improve performance.

Which solution improves function performance?

## Options

A. Increase the Lambda function memory.

B. Store configuration in Lambda environment variables.

C. Use provisioned concurrency.

D. Enable Lambda function URL.

## Correct Answer

**B. Store configuration in Lambda environment variables.**

## Explanation

Lambda environment variables are loaded when the function is initialized. Storing configuration data as environment variables eliminates the need for database calls, reducing latency.

### Why other options are incorrect:

- **A** - Memory affects compute, not data retrieval.

- **C** - Provisioned concurrency reduces cold starts.

- **D** - Function URL is for HTTP access.

## References

- https://docs.aws.amazon.com/lambda/latest/dg/configuration-envvars.html
- https://tutorialsdojo.com/aws-lambda/

## Domain

Design High-Performing Architectures
