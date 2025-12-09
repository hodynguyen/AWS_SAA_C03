# Question 2

A company is using AWS Fargate to run a batch job whenever an object is uploaded to an Amazon S3 bucket. The minimum ECS task count is initially set to 1 to save on costs and should only be increased based on new objects uploaded to the S3 bucket.

Which is the most suitable option to implement with the LEAST amount of effort?

## Options

A. Set up an Amazon EventBridge (Amazon CloudWatch Events) rule to detect S3 object PUT operations and set the target to a Lambda function that will run the StartTask API command.

B. Set up an alarm in CloudWatch to monitor S3 object-level operations recorded on CloudTrail. Set two alarm actions to update the ECS task count to scale-out/scale-in depending on the S3 event.

C. Set up an Amazon EventBridge (Amazon CloudWatch Events) rule to detect S3 object PUT operations and set the target to the ECS cluster to run a new ECS task.

D. Set up an alarm in Amazon CloudWatch to monitor S3 object-level operations that are recorded on CloudTrail. Create an Amazon EventBridge (Amazon CloudWatch Events) rule that triggers the ECS cluster when new CloudTrail events are detected.

## Correct Answer

**C. Set up an Amazon EventBridge (Amazon CloudWatch Events) rule to detect S3 object PUT operations and set the target to the ECS cluster to run a new ECS task.**

## Explanation

Amazon EventBridge (Amazon CloudWatch Events) is a serverless event bus that makes it easy to connect applications together. It uses data from your own applications, integrated software as a service (SaaS) applications, and AWS services. This simplifies the process of building event-driven architectures by decoupling event producers from event consumers.

You can use Amazon EventBridge to run Amazon ECS tasks when certain AWS events occur. You can set up an EventBridge rule that runs an Amazon ECS task whenever a file is uploaded to a certain Amazon S3 bucket using the Amazon S3 PUT operation.

### Why other options are incorrect:

- **A** - Although this solution meets the requirement, creating your own Lambda function for this scenario is not really necessary. It is much simpler to control ECS tasks directly as targets for the CloudWatch Event rule.

- **D** - Using CloudTrail and CloudWatch Alarm creates unnecessary complexity. Amazon EventBridge can directly target an ECS task on the Targets section when you create a new rule.

- **B** - You can't directly set CloudWatch Alarms to update the ECS task count.

## References

- https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/CloudWatch-Events-tutorial-ECS.html
- https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/Create-CloudWatch-Events-Rule.html
- https://tutorialsdojo.com/amazon-cloudwatch/

## Domain

Design Cost-Optimized Architectures
