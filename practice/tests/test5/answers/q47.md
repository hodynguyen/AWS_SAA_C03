# Question 47

SNS fanout to SQS queues. EC2 Spot instance terminated while processing. What happens to the message?

## Options

A. Message deleted and duplicated when instance comes online.

B. Message sent to Dead Letter Queue in DataSync.

C. Message assigned to same instance when it comes back.

D. Message becomes available for other instances after visibility timeout expires.

## Correct Answer

**D. Message becomes available for other instances after visibility timeout expires.**

## Explanation

SQS message lifecycle:
- **Consumer receives**: Message becomes invisible
- **Processing incomplete**: Consumer doesn't delete message
- **Timeout expires**: Message becomes visible again
- **Other consumers**: Can pick up the message

### Why other options are incorrect:

- **A** - Message isn't deleted; no duplication mechanism.

- **B** - DataSync is for data transfer, not SQS DLQ.

- **C** - No affinity between message and specific instance.

## References

- https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-visibility-timeout.html
- https://tutorialsdojo.com/amazon-sqs/

## Domain

Design High-Performing Architectures
