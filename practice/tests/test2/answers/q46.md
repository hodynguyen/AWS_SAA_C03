# Question 46

A company runs a mobile gaming application that uses Amazon DynamoDB as its data store. The game has spiked in popularity and the development team needs to reduce response times. Read requests on specific items are much more common than write requests.

Which solution provides the lowest latency for repeated reads?

## Options

A. Enable DynamoDB Accelerator (DAX).

B. Enable DynamoDB Auto Scaling.

C. Enable DynamoDB Global Tables.

D. Enable DynamoDB Streams.

## Correct Answer

**A. Enable DynamoDB Accelerator (DAX).**

## Explanation

Amazon DynamoDB Accelerator (DAX) is a fully managed, highly available, in-memory cache for DynamoDB that delivers up to a 10x performance improvement from milliseconds to microseconds.

### Why other options are incorrect:

- **B** - Auto Scaling handles capacity, not latency.

- **C** - Global Tables is for multi-region replication.

- **D** - Streams is for change data capture.

## References

- https://aws.amazon.com/dynamodb/dax/
- https://tutorialsdojo.com/amazon-dynamodb/

## Domain

Design High-Performing Architectures
