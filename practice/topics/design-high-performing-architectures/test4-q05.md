# Question 5

An ECS Cluster processes financial data and stores results in a DynamoDB table. A solution is needed to detect new entries and automatically trigger a Lambda function for verification tests.

What solution provides automatic triggers with minimal configuration changes?

## Options

A. Use CloudWatch Alarms to trigger the Lambda function whenever a new entry is created in the DynamoDB table.

B. Enable DynamoDB Streams to capture table activity and automatically trigger the Lambda function.

C. Invoke the Lambda functions using SNS each time that the ECS Cluster successfully processed financial data.

D. Use Systems Manager Automation to detect new entries in the DynamoDB table then automatically invoke the Lambda function for processing.

## Correct Answer

**B. Enable DynamoDB Streams to capture table activity and automatically trigger the Lambda function.**

## Explanation

DynamoDB Streams captures table modifications in real-time. When enabled, you can associate a Lambda function directly with the stream ARN. AWS Lambda automatically polls the stream and invokes your function synchronously when new records appear—no additional services needed.

### Why other options are incorrect:

- **A** - CloudWatch Alarms monitor metrics (CPU, memory), not data changes in DynamoDB tables.

- **C** - Adding SNS adds unnecessary complexity. DynamoDB Streams provides direct Lambda integration.

- **D** - Systems Manager Automation manages EC2 maintenance tasks, not DynamoDB monitoring.

## References

- https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Streams.Lambda.html
- https://tutorialsdojo.com/amazon-dynamodb/

## Domain

Design High-Performing Architectures
