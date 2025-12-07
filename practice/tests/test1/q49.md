# Question 49

A car dealership website hosted in Amazon EC2 stores car listings in an Amazon Aurora database managed by Amazon RDS. Once a vehicle has been sold, its data must be removed from the current listings and forwarded to a distributed processing system.

Which of the following options can satisfy the given requirement?

## Options

A. Create an RDS event subscription and send the notifications to AWS Lambda. Configure the Lambda function to fan out the event notifications to multiple Amazon SQS queues.

B. Create an RDS event subscription and send the notifications to Amazon SQS. Configure the SQS queues to fan out the event notifications to multiple Amazon SNS topics.

C. Create a native function or a stored procedure that invokes an AWS Lambda function. Configure the Lambda function to send event notifications to an Amazon SQS queue for the processing system to consume.

D. Create an RDS event subscription and send the notifications to Amazon SNS. Configure the SNS topic to fan out the event notifications to multiple Amazon SQS queues.

## Correct Answer

**C. Create a native function or a stored procedure that invokes an AWS Lambda function. Configure the Lambda function to send event notifications to an Amazon SQS queue for the processing system to consume.**

## Explanation

You can invoke an AWS Lambda function from an Amazon Aurora MySQL-Compatible Edition DB cluster with a native function or a stored procedure. This is useful when you want to integrate your database with other AWS services.

You can trigger a Lambda function whenever a listing is deleted from the database, then write the logic to send the listing data to an SQS queue for processing.

### Why other options are incorrect:

- **A, B, D** - RDS event subscriptions notify about operational changes (infrastructure-level), not data modifications like INSERT, DELETE, or UPDATE.

## References

- https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/AuroraMySQL.Integrating.Lambda.html
- https://aws.amazon.com/blogs/database/capturing-data-changes-in-amazon-aurora-using-aws-lambda/
- https://tutorialsdojo.com/amazon-aurora/

## Domain

Design High-Performing Architectures
