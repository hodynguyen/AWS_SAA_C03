# Question 50

A company is using Amazon S3 to store frequently accessed data. When an object is created or deleted, the S3 bucket will send an event notification to the Amazon SQS queue. A solutions architect needs to create a solution that will notify the development and operations team about the created or deleted objects.

Which of the following would satisfy this requirement?

## Options

A. Create an Amazon SNS topic and configure two SQS queues to subscribe to the topic. Grant S3 permission to send notifications to SNS and update the bucket to use the new SNS topic.

B. Set up an Amazon SNS topic and configure two SQS queues to poll the SNS topic.

C. Create a new Amazon SNS FIFO topic for the other team. Grant S3 permission to send the notification to the second SNS topic.

D. Set up another SQS queue for the other team. Grant S3 permission to send a notification to the second SQS queue.

## Correct Answer

**A. Create an Amazon SNS topic and configure two SQS queues to subscribe to the topic. Grant S3 permission to send notifications to SNS and update the bucket to use the new SNS topic.**

## Explanation

Amazon S3 event notifications are designed to be delivered at least once and to one destination only. You cannot attach two or more SNS topics or SQS queues for S3 event notification.

Using the message fanout pattern, you can create an SNS topic and have multiple SQS queues subscribe to it. When SNS receives an event notification, it publishes the message to all subscribers.

### Why other options are incorrect:

- **D** - You can only add 1 SQS or SNS at a time for S3 event notification.

- **C** - Same as above, you can only use one destination for S3 events.

- **B** - You can't poll Amazon SNS. SQS queues must subscribe to the SNS topic.

## References

- https://docs.aws.amazon.com/AmazonS3/latest/dev/NotificationHowTo.html
- https://docs.aws.amazon.com/sns/latest/dg/welcome.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design High-Performing Architectures
