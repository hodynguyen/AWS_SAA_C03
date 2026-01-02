# Question 46

SQS queue is used for batch processing. What prevents other consumers from receiving a message being processed?

## Options

A. Visibility Timeout

B. Component Timeout

C. Processing Timeout

D. Receiving Timeout

## Correct Answer

**A. Visibility Timeout**

## Explanation

Visibility Timeout:
- **Prevents reprocessing**: Hides message from other consumers
- **Default 30 seconds**: Configurable up to 12 hours
- **Consumer must delete**: After successful processing
- **Auto-release**: Message returns to queue if not deleted

### Why other options are incorrect:

- **B, C, D** - These are not SQS concepts.

## References

- https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-visibility-timeout.html
- https://tutorialsdojo.com/amazon-sqs/

## Domain

Design Resilient Architectures
