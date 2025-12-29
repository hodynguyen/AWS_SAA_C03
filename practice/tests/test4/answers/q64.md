# Question 64

A messaging service expects thousands of messages daily for AI training on EMR. Messages must not be lost, no duplicates, and processed in order of arrival.

Which option satisfies these requirements?

## Options

A. Create an Amazon Data Firehose.

B. Set up a default Amazon SQS queue.

C. Create an Amazon Kinesis Data Stream.

D. Set up an Amazon SNS Topic.

## Correct Answer

**C. Create an Amazon Kinesis Data Stream.**

## Explanation

Kinesis Data Streams provides:
- **Ordered delivery**: Records within a shard maintain sequence
- **Durability**: Data replicated across 3 AZs, retained 24 hours (up to 365 days)
- **Exactly-once semantics**: With proper consumer checkpointing
- **High throughput**: Handles thousands of records per second

### Why other options are incorrect:

- **A** - Firehose delivers to destinations but doesn't guarantee order.

- **B** - Standard SQS doesn't guarantee order or exactly-once delivery.

- **D** - SNS is pub/sub with at-least-once delivery, no ordering.

## References

- https://docs.aws.amazon.com/streams/latest/dev/introduction.html
- https://tutorialsdojo.com/amazon-kinesis/

## Domain

Design High-Performing Architectures
