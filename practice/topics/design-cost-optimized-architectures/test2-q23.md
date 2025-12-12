# Question 23

A company is building an internal application that allows users to upload images. Each upload request must be sent to Amazon Kinesis Data Streams for processing before the pictures are stored in an Amazon S3 bucket. The application should immediately return a success message to the user after the upload, while the downstream processing is handled asynchronously.

Which solution will enable asynchronous processing from Kinesis to S3 in the most cost-effective way?

## Options

A. Use Kinesis Data Streams with AWS Lambda consumers to asynchronously process records and write them to S3.

B. Send data from Kinesis Data Streams to Amazon Data Firehose and configure it to deliver directly to S3.

C. Use a combination of Amazon SQS to queue the requests and then asynchronously process them using On-Demand Amazon EC2 Instances.

D. Use a combination of AWS Lambda and Step Functions to orchestrate service components and asynchronously process the requests.

## Correct Answer

**A. Use Kinesis Data Streams with AWS Lambda consumers to asynchronously process records and write them to S3.**

## Explanation

AWS Lambda supports both synchronous and asynchronous invocation. For Amazon Kinesis Data Streams, AWS Lambda uses an event source mapping to poll the stream, batch records, invoke the function, and manage checkpoints.

This serverless integration is cost-effective because Lambda scales automatically and only incurs costs for actual invocations.

### Why other options are incorrect:

- **D** - Step Functions adds unnecessary cost and complexity.

- **C** - EC2 requires provisioning and managing instances.

- **B** - Firehose has buffering constraints not ideal for this use case.

## References

- https://docs.aws.amazon.com/lambda/latest/dg/welcome.html
- https://tutorialsdojo.com/aws-lambda/

## Domain

Design Cost-Optimized Architectures
