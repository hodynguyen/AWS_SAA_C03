# Question 29

An order processing system uses a standard SQS queue. Orders are sometimes processed twice, causing customer issues.

How can you prevent duplicate processing?

## Options

A. Use an SQS FIFO Queue instead.

B. Alter the retention period in SQS.

C. Change the message size in SQS.

D. Alter the visibility timeout of SQS.

## Correct Answer

**A. Use an SQS FIFO Queue instead.**

## Explanation

FIFO (First-In-First-Out) queues provide exactly-once processing:
- **Deduplication**: Messages with the same deduplication ID are rejected within 5-minute window
- **Message sequencing**: Messages are processed in exact order received
- **No duplicates**: Each message is delivered exactly once

Standard queues offer at-least-once delivery, which can result in duplicates.

### Why other options are incorrect:

- **B** - Retention period controls how long messages stay in queue, not duplication.

- **C** - Message size has no impact on duplicate processing.

- **D** - Visibility timeout prevents re-processing during processing, but doesn't guarantee exactly-once.

## References

- https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/FIFO-queues-exactly-once-processing.html
- https://tutorialsdojo.com/amazon-sqs/

## Domain

Design High-Performing Architectures
