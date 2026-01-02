# Question 64

Batch job processes SQS messages weekly. After 2 weeks, not all messages are processed.

What is the root cause?

## Options

A. Long polling configured.

B. Missing SQS permissions.

C. Messages exceeded retention period (auto-deleted).

D. Short polling configured.

## Correct Answer

**C. Messages exceeded retention period (auto-deleted).**

## Explanation

SQS message retention:
- **Default**: 4 days
- **Maximum**: 14 days
- **Auto-deletion**: Messages older than retention period deleted

Weekly processing means messages wait 7 days, exceeding 4-day default.

### Why other options are incorrect:

- **A** - Long polling is about receiving efficiency, not message loss.

- **B** - Permission issues would prevent any processing.

- **D** - Short polling affects efficiency, not message retention.

## References

- https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-message-lifecycle.html
- https://tutorialsdojo.com/amazon-sqs/

## Domain

Design High-Performing Architectures
