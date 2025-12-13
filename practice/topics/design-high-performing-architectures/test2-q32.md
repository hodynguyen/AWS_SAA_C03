# Question 32

An insurance company plans to implement a message filtering feature in its web application. To implement this solution, it needs to create separate Amazon SQS queues for each type of quote request. The entire message processing should not exceed 24 hours.

Which of the following solutions should be implemented to meet the above requirement?

## Options

A. Create a data stream in Amazon Kinesis Data Streams. Use the Kinesis Client Library to deliver all the records to the designated SQS queues.

B. Create one Amazon SNS topic and configure the SQS queues to subscribe to the SNS topic. Publish the same messages to all SQS queues. Filter the messages in each queue.

C. Create one Amazon SNS topic and configure the SQS queues to subscribe to the SNS topic. Set the filter policies in the SNS subscriptions to publish the message to the designated SQS queue.

D. Create multiple Amazon SNS topics and configure the SQS queues to subscribe to the SNS topics.

## Correct Answer

**C. Create one Amazon SNS topic and configure the SQS queues to subscribe to the SNS topic. Set the filter policies in the SNS subscriptions to publish the message to the designated SQS queue based on its quote request type.**

## Explanation

Amazon SNS message filtering assigns a filter policy to the topic subscription, and the subscriber will only receive messages they are interested in. This method is known as fanout to Amazon SQS queues.

### Why other options are incorrect:

- **B** - Publishing same messages to all queues defeats filtering purpose.

- **D** - Multiple SNS topics is unnecessary complexity.

- **A** - Kinesis Data Streams is not a message filtering service.

## References

- https://aws.amazon.com/getting-started/hands-on/filter-messages-published-to-topics/
- https://tutorialsdojo.com/amazon-sns/

## Domain

Design High-Performing Architectures
