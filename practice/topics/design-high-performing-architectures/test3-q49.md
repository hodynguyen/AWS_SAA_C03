# Question 49

## Topic
Design High-Performing Architectures

## Question
A company is storing its financial reports and regulatory documents in an Amazon S3 bucket. To comply with the IT audit, they tasked their Solutions Architect to track all new objects added to the bucket as well as the removed ones. It should also track whether a versioned object is permanently deleted. The Architect must configure Amazon S3 to publish notifications for these events to a queue for post-processing and to an Amazon SNS topic that will notify the Operations team.

Which of the following is the MOST suitable solution that the Architect should implement?

## Options
A. Create a new Amazon SNS topic and Amazon MQ. Add an S3 event notification configuration on the bucket to publish s3:ObjectCreated:* and ObjectRemoved:DeleteMarkerCreated event types to SQS and SNS.

B. Create a new Amazon SNS topic and Amazon SQS queue. Add an S3 event notification configuration on the bucket to publish s3:ObjectCreated:* and ObjectRemoved:DeleteMarkerCreated event types to SQS and SNS.

C. Create a new Amazon SNS topic and Amazon SQS queue. Add an S3 event notification configuration on the bucket to publish s3:ObjectCreated:* and s3:ObjectRemoved:Delete event types to SQS and SNS.

D. Create a new Amazon SNS topic and Amazon MQ. Add an S3 event notification configuration on the bucket to publish s3:ObjectAdded:* and s3:ObjectRemoved:* event types to SQS and SNS.

## Correct Answer
C

## Explanation
The Amazon S3 notification feature enables you to receive notifications when certain events happen in your bucket. To enable notifications, you must first add a notification configuration that identifies the events you want Amazon S3 to publish and the destinations where you want Amazon S3 to send the notifications. You store this configuration in the notification subresource that is associated with a bucket. Amazon S3 provides an API for you to manage this subresource.

Amazon S3 event notifications typically deliver events in seconds but can sometimes take a minute or longer. If two writes are made to a single non-versioned object at the same time, it is possible that only a single event notification will be sent. If you want to ensure that an event notification is sent for every successful write, you can enable versioning on your bucket. With versioning, every successful write will create a new version of your object and will also send an event notification.

Amazon S3 can publish notifications for the following events:
1. New object-created events
2. Object removal events
3. Restore object events
4. Reduced Redundancy Storage (RRS) object lost events
5. Replication events

Amazon S3 supports the following destinations where it can publish events:
1. Amazon Simple Notification Service (Amazon SNS) topic
2. Amazon Simple Queue Service (Amazon SQS) queue
3. AWS Lambda

Hence, the correct answer is: Create a new Amazon SNS topic and Amazon SQS queue. Add an S3 event notification configuration on the bucket to publish s3:ObjectCreated:* and s3:ObjectRemoved:Delete event types to SQS and SNS.

The option that says: Create a new Amazon SNS topic and Amazon MQ. Add an S3 event notification configuration on the bucket to publish s3:ObjectAdded:* and s3:ObjectRemoved:* event types to SQS and SNS is incorrect. There is no s3:ObjectAdded:* type in Amazon S3. You should add an S3 event notification configuration on the bucket to publish events of the s3:ObjectCreated:* type instead. Moreover, Amazon S3 does support Amazon MQ as a destination to publish events.

The option that says: Create a new Amazon SNS topic and Amazon SQS queue. Add an S3 event notification configuration on the bucket to publish s3:ObjectCreated:* and ObjectRemoved:DeleteMarkerCreated event types to SQS and SNS is incorrect because the s3:ObjectRemoved:DeleteMarkerCreated type is only triggered when a delete marker is created for a versioned object and not when an object is deleted or a versioned object is permanently deleted.

The option that says: Create a new Amazon SNS topic and Amazon MQ. Add an S3 event notification configuration on the bucket to publish s3:ObjectCreated:* and ObjectRemoved:DeleteMarkerCreated event types to SQS and SNS is incorrect because Amazon S3 does public event messages to Amazon MQ. You should use an Amazon SQS instead. In addition, the s3:ObjectRemoved:DeleteMarkerCreated type is only triggered when a delete marker is created for a versioned object. Remember that the scenario asked to publish events when an object is deleted or a versioned object is permanently deleted.

## References
- https://docs.aws.amazon.com/AmazonS3/latest/dev/NotificationHowTo.html
- https://docs.aws.amazon.com/AmazonS3/latest/dev/ways-to-add-notification-config-to-bucket.html
- https://aws.amazon.com/blogs/aws/s3-event-notification/
- https://tutorialsdojo.com/amazon-s3/
