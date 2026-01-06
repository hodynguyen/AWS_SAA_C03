# Question 46

IoT sensor data. Real-time ingest with millisecond response times.

Which is the best solution?

## Options

A. Kinesis Data Streams + Lambda + DynamoDB.

B. Kinesis Data Firehose + Lambda + DynamoDB.

C. Kinesis Data Streams + Lambda + Redshift.

D. SQS + Lambda + Redshift.

## Correct Answer

**A. Kinesis Data Streams + Lambda + DynamoDB.**

## Explanation

Real-time IoT processing:
- **Kinesis Data Streams**: Real-time ingestion
- **Lambda**: Process data
- **DynamoDB**: Millisecond response times
- **Scalable**: Handle any volume

### Why other options are incorrect:

- **B** - Firehose doesn't support DynamoDB destination.

- **C** - Redshift has sub-second latency, not millisecond.

- **D** - SQS not optimized for real-time streaming.

## References

- https://aws.amazon.com/kinesis/data-streams/faqs/
- https://tutorialsdojo.com/amazon-kinesis/

## Domain

Design High-Performing Architectures
