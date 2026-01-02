# Question 6

A ticketing service uses SQS with EC2 instances polling as often as possible. This causes unnecessary CPU cycles and increased costs due to empty responses.

What should be done to make the system more cost-effective?

## Options

A. Configure SQS long polling with ReceiveMessageWaitTimeSeconds > 0.

B. Configure SQS long polling with ReceiveMessageWaitTimeSeconds = 0.

C. Configure SQS short polling with ReceiveMessageWaitTimeSeconds = 0.

D. Configure SQS short polling with ReceiveMessageWaitTimeSeconds > 0.

## Correct Answer

**A. Configure SQS long polling with ReceiveMessageWaitTimeSeconds > 0.**

## Explanation

Long polling:
- **ReceiveMessageWaitTimeSeconds > 0**: Wait up to 20 seconds for messages
- **Reduces empty responses**: Only returns when messages available or timeout
- **Lowers costs**: Fewer API calls = lower SQS costs
- **Queries all servers**: More complete results

Short polling (value = 0) returns immediately, causing many empty responses.

### Why other options are incorrect:

- **B, C** - ReceiveMessageWaitTimeSeconds = 0 is short polling (the current problem).

- **D** - Short polling can't have wait time > 0; that would be long polling.

## References

- https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-long-polling.html
- https://tutorialsdojo.com/amazon-sqs/

## Domain

Design High-Performing Architectures
