# Question 26

A media company is setting up an ECS batch architecture for its image processing application. It will be hosted in an Amazon ECS Cluster with two ECS tasks that will handle image uploads from the users and image processing. The first ECS task will process the user requests, store the image in an S3 input bucket, and push a message to a queue. The second task reads from the queue, parses the message containing the object name, and then downloads the object.

Which of the following should the Architect do next?

## Options

A. Launch a new Amazon Data Firehose and configure the second ECS task to read from it. Create an IAM role that the ECS tasks can assume to get access to the S3 buckets and Data Firehose. Specify the ARN of the IAM Role in the taskDefinitionArn field.

B. Launch a new Amazon SQS queue and configure the second ECS task to read from it. Create an IAM role that the ECS tasks can assume to get access to the S3 buckets and SQS queue. Declare the IAM Role (taskRoleArn) in the task definition.

C. Launch a new Amazon AppStream 2.0 queue and configure the second ECS task to read from it.

D. Launch a new Amazon MQ queue and configure the second ECS task to read from it. Set the (EnableTaskIAMRole) option to true.

## Correct Answer

**B. Launch a new Amazon SQS queue and configure the second ECS task to read from it. Create an IAM role that the ECS tasks can assume to get access to the S3 buckets and SQS queue. Declare the IAM Role (taskRoleArn) in the task definition.**

## Explanation

Amazon SQS is ideal for batch processing workloads. ECS tasks can assume IAM roles to access S3 and SQS. The taskRoleArn in the task definition specifies which role the container can use.

### Why other options are incorrect:

- **C** - AppStream 2.0 is for application streaming, not queuing.

- **A** - Data Firehose is for streaming data, not batch processing.

- **D** - Amazon MQ is a message broker, not a queue service.

## References

- https://docs.aws.amazon.com/AmazonECS/latest/developerguide/common_use_cases.html
- https://tutorialsdojo.com/amazon-sqs/

## Domain

Design High-Performing Architectures
