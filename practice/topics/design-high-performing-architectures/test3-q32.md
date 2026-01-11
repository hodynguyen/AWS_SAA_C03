# Question 32

## Topic
Design High-Performing Architectures

## Question
A Solutions Architect needs to deploy a mobile application that collects votes for a singing competition. Millions of users from around the world will submit votes using their mobile phones. These votes must be collected and stored in a highly scalable and highly available database which will be queried for real-time ranking. The database is expected to undergo frequent schema changes throughout the voting period.

Which of the following combination of services should the architect use to meet this requirement?

## Options
A. Amazon Aurora and Amazon Cognito

B. Amazon DocumentDB (with MongoDB compatibility) and Amazon AppFlow

C. Amazon DynamoDB and AWS AppSync

D. Amazon Relational Database Service (RDS) and Amazon MQ

## Correct Answer
C

## Explanation
Amazon DynamoDB is a fully managed, serverless, key-value NoSQL database designed to run high-performance applications at any scale. DynamoDB tables are schemaless—other than the primary key, you do not need to define any extra attributes or data types when you create a table, which is why it's suitable for data with frequently changing schema.

You can use AppSync with DynamoDB to make it easy to build collaborative apps that keep shared data updated in real-time.

**Why other options are incorrect:**
- **Option A** is incorrect because Aurora is a relational database not suited for frequently changing schemas.
- **Option B** is incorrect because AppFlow cannot interface with DocumentDB for real-time updates.
- **Option D** is incorrect because RDS is impractical for frequently changing schemas.

## References
- https://aws.amazon.com/dynamodb/faqs/
- https://aws.amazon.com/appsync/
- https://tutorialsdojo.com/amazon-dynamodb/
