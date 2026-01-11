# Question 21

## Topic
Design High-Performing Architectures

## Question
A company currently has an Augment Reality (AR) mobile game that has a serverless backend. It is using a DynamoDB table which was launched using the AWS CLI to store all the user data and information gathered from the players and a Lambda function to pull the data from DynamoDB. The game is being used by millions of users each day to read and store data.

How would you design the application to improve its overall performance and make it more scalable while keeping the costs low? (Select TWO.)

## Options
A. Configure CloudFront with DynamoDB as the origin; cache frequently accessed data on the client device using ElastiCache.

B. Enable DynamoDB Accelerator (DAX) and ensure that the Auto Scaling is enabled and increase the maximum provisioned read and write capacity.

C. Since Auto Scaling is enabled by default, the provisioned read and write capacity will adjust automatically. Also enable DynamoDB Accelerator (DAX) to improve the performance from milliseconds to microseconds.

D. Use API Gateway in conjunction with Lambda and turn on the caching on frequently accessed data and enable DynamoDB global replication.

E. Use AWS IAM Identity Center to authenticate users and have them directly access DynamoDB using single sign-on.

## Correct Answers
**B. Enable DynamoDB Accelerator (DAX) and ensure that the Auto Scaling is enabled and increase the maximum provisioned read and write capacity.**

**D. Use API Gateway in conjunction with Lambda and turn on the caching on frequently accessed data and enable DynamoDB global replication.**

## Explanation
Amazon DynamoDB Accelerator (DAX) is a fully managed, highly available, in-memory cache for DynamoDB that delivers up to a 10x performance improvement – from milliseconds to microseconds.

Amazon API Gateway handles all the tasks involved in accepting and processing up to hundreds of thousands of concurrent API calls. AWS Lambda scales your functions automatically on your behalf.

**Why other options are incorrect:**
- **Option A** is incorrect because you cannot integrate DynamoDB with CloudFront as the origin.
- **Option C** is incorrect because Auto Scaling is not enabled by default in DynamoDB tables created using AWS CLI.
- **Option E** is incorrect because IAM Identity Center is for access management, not for scalability.

## References
- https://aws.amazon.com/lambda/faqs/
- https://aws.amazon.com/api-gateway/faqs/
- https://aws.amazon.com/dynamodb/dax/
