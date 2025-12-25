# Question 24

## Topic
Design High-Performing Architectures

## Question
A company has a team of developers that provisions its own resources on the AWS cloud. The developers use IAM user access keys to automate resource provisioning and application testing processes in AWS. To ensure proper security compliance, the security team wants to automate the process of deactivating and deleting any IAM user access key that is over 90 days old.

Which solution will meet these requirements with the LEAST operational effort?

## Options
A. Use the AWS Config managed rule to check if the IAM user access keys are not rotated within 90 days. Create an Amazon EventBridge rule for the non-compliant keys, and define a target to invoke a custom AWS Lambda function to deactivate and delete the keys.

B. Create an Amazon EventBridge rule to filter IAM user access keys older than 90 days. Schedule an AWS Batch job that runs every 24 hours to delete all the specified access keys.

C. Create a custom AWS Config rule to check the max-age of IAM access keys. Use Amazon EventBridge Scheduler to invoke an AWS Batch job every 24 hours to delete all non-compliant access keys.

D. Create an Amazon EventBridge rule to filter IAM user access keys older than 90 days. Define a target to invoke an AWS Lambda function to deactivate and delete the old access keys.

## Correct Answer
A

## Explanation
AWS Config provides a detailed view of the configuration of AWS resources in your AWS account. This includes how the resources are related to one another and how they were configured in the past so that you can see how the configurations and relationships change over time.

You can use AWS Config rules to evaluate the configuration settings of your AWS resources. When AWS Config detects that a resource violates the conditions in one of your rules, AWS Config flags the resource as non-compliant and sends a notification. AWS Config continuously evaluates your resources as they are created, changed, or deleted.

To analyze potential security weaknesses, you need detailed historical information about your AWS resource configurations, such as the AWS Identity and Access Management (IAM) permissions that are granted to your users or the Amazon EC2 security group rules that control access to your resources.

Amazon EventBridge is a serverless event bus service that you can use to connect your applications with data from a variety of sources.

You can use an Amazon EventBridge rule with a custom event pattern and an input transformer to match an AWS Config evaluation rule output as NON_COMPLIANT. Then, route the response to an Amazon Simple Notification Service (Amazon SNS) topic.

Amazon EventBridge rule for checking IAM access key architecture

Therefore, the correct answer is: Use the AWS Config managed rule to check if the IAM user access keys are not rotated within 90 days. Create an Amazon EventBridge rule for the non-compliant keys, and define a target to invoke a custom AWS Lambda function to deactivate and delete the keys. Amazon EventBridge can check for AWS Config non-compliant events and then trigger a Lambda for remediation.

References:

https://aws.amazon.com/blogs/mt/managing-aged-access-keys-through-aws-config-remediations/

https://aws.amazon.com/premiumsupport/knowledge-center/config-resource-non-compliant/

https://docs.aws.amazon.com/config/latest/developerguide/how-does-config-work.html

Check out these Amazon EventBridge and AWS Config Cheat Sheets:

https://tutorialsdojo.com/amazon-eventbridge/

https://tutorialsdojo.com/aws-config/

**Why other options are incorrect:**

- The option that says: Create an Amazon EventBridge rule to filter IAM user access keys older than 90 days. Schedule an AWS Batch job that runs every 24 hours to delete all the specified access keys is incorrect. Amazon EventBridge cannot directly check for IAM events that show the age of IAM access keys. The use of the AWS Batch service is not warranted here as it is primarily used to easily and efficiently run hundreds of thousands of batch computing jobs on AWS.

- The option that says: Create a custom AWS Config rule to check the max-age of IAM access keys. Use Amazon EventBridge Scheduler to invoke an AWS Batch job every 24 hours to delete all non-compliant access keys is incorrect because it makes the solution more complex. Creating a custom Config rule is just unnecessary since a managed rule already exists for access key rotation. Also, using an AWS Batch to delete access keys adds extra setup and maintenance compared to using a simple Lambda function.

- The option that says: Create an Amazon EventBridge rule to filter IAM user access keys older than 90 days. Define a target to invoke an AWS Lambda function to deactivate and delete the old access keys is incorrect. Amazon EventBridge cannot directly check for IAM events that contain the age of IAM access keys. You must use the AWS Config service to detect the non-compliant IAM keys.

