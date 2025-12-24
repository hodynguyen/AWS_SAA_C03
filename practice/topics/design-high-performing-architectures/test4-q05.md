# Question 5

## Topic
Design High-Performing Architectures

## Question
A leading IT consulting company has an application which processes a large stream of financial data by an Amazon ECS Cluster then stores the result to a DynamoDB table. You have to design a solution to detect new entries in the DynamoDB table then automatically trigger a Lambda function to run some tests to verify the processed data.

What solution can be easily implemented to alert the Lambda function of new entries while requiring minimal configuration change to your architecture?

## Options
A. Use CloudWatch Alarms to trigger the Lambda function whenever a new entry is created in the DynamoDB table.

B. Enable DynamoDB Streams to capture table activity and automatically trigger the Lambda function.

C. Invoke the Lambda functions using SNS each time that the ECS Cluster successfully processed financial data.

D. Use Systems Manager Automation to detect new entries in the DynamoDB table then automatically invoke the Lambda function for processing.

## Correct Answer
B

## Explanation
Amazon DynamoDB is integrated with AWS Lambda so that you can create triggers—pieces of code that automatically respond to events in DynamoDB Streams. With triggers, you can build applications that react to data modifications in DynamoDB tables.

If you enable DynamoDB Streams on a table, you can associate the stream ARN with a Lambda function that you write. Immediately after an item in the table is modified, a new record appears in the table's stream. AWS Lambda polls the stream and invokes your Lambda function synchronously when it detects new stream records.

You can create a Lambda function which can perform a specific action that you specify, such as sending a notification or initiating a workflow. For instance, you can set up a Lambda function to simply copy each stream record to persistent storage, such as EFS or S3, to create a permanent audit trail of write activity in your table.

Suppose you have a mobile gaming app that writes to a TutorialsDojoCourses table. Whenever the TopCourse attribute of the TutorialsDojoScores table is updated, a corresponding stream record is written to the table's stream. This event could then trigger a Lambda function that posts a congratulatory message on a social media network. (The function would simply ignore any stream records that are not updated to TutorialsDojoCourses or that do not modify the TopCourse attribute.)

Hence, enabling DynamoDB Streams to capture table activity and automatically trigger the Lambda function is the correct answer because the requirement can be met with minimal configuration change using DynamoDB streams, which can automatically trigger Lambda functions whenever there is a new entry.

Using CloudWatch Alarms to trigger the Lambda function whenever a new entry is created in the DynamoDB table is incorrect because CloudWatch Alarms only monitor service metrics, not changes in DynamoDB table data.

Invoking the Lambda functions using SNS each time that the ECS Cluster successfully processed financial data is incorrect because you don't need to create an SNS topic just to invoke Lambda functions. You can enable DynamoDB streams instead to meet the requirement with less configuration.

Using Systems Manager Automation to detect new entries in the DynamoDB table then automatically invoking the Lambda function for processing is incorrect because the Systems Manager Automation service is primarily used to simplify common maintenance and deployment tasks of Amazon EC2 instances and other AWS resources. It does not have the capability to detect new entries in a DynamoDB table.

References:

https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Streams.Lambda.html

https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Streams.html

Check out this Amazon DynamoDB cheat sheet:

https://tutorialsdojo.com/amazon-dynamodb/


