# Question 43

IoT sensors to Kinesis (default settings) to S3 every 3 days. Only 1 day of data in S3.

What is the MOST likely cause?

## Options

A. Default Kinesis retention is 24 hours.

B. Someone deleted S3 data.

C. S3 data loss.

D. Insufficient Kinesis access to S3.

## Correct Answer

**A. Default Kinesis retention is 24 hours.**

## Explanation

Kinesis data retention:
- **Default 24 hours**: Data expires after this
- **Extended retention**: Up to 7 days (extra cost)
- **365 days max**: With Long-term retention
- **Solution**: Increase retention period

### Why other options are incorrect:

- **B** - Would show in CloudTrail if deleted.

- **C** - S3 has 99.999999999% durability.

- **D** - If access issue, no data would appear.

## References

- https://aws.amazon.com/kinesis/data-streams/faqs/
- https://tutorialsdojo.com/amazon-kinesis/

## Domain

Design Resilient Architectures
