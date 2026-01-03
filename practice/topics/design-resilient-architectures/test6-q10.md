# Question 10

Lambda function handles HTTP POST from third-party analytics service webhook.

What is the MOST operationally efficient solution?

## Options

A. SQS queue URL as webhook.

B. API Gateway endpoint as webhook.

C. Lambda Function URL as webhook.

D. EC2 proxy with public IP as webhook.

## Correct Answer

**C. Lambda Function URL as webhook.**

## Explanation

Lambda Function URL:
- **Direct HTTP endpoint**: No intermediary needed
- **Simple setup**: One-click in console or CLI
- **Unique URL**: Generated per function
- **Less overhead**: No API Gateway management

### Why other options are incorrect:

- **A** - SQS doesn't accept external HTTP requests.

- **B** - Works but more complex than Function URL.

- **D** - EC2 adds unnecessary management overhead.

## References

- https://docs.aws.amazon.com/lambda/latest/dg/lambda-urls.html
- https://tutorialsdojo.com/aws-lambda/

## Domain

Design Resilient Architectures
