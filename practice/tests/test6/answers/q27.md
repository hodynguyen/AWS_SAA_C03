# Question 27

Kinesis Data Stream + Lambda system is slow as data rate increases.

What should be done to improve performance?

## Options

A. Decrease shards using MergeShard.

B. Increase shards using UpdateShardCount.

C. Implement Step Scaling.

D. Replace with Data Firehose.

## Correct Answer

**B. Increase shards using UpdateShardCount.**

## Explanation

Kinesis resharding:
- **More shards**: Higher throughput capacity
- **UpdateShardCount**: API to add shards
- **Scales without limits**: Just add more shards
- **Cost**: Pay per shard-hour

### Why other options are incorrect:

- **A** - Decreasing shards reduces capacity.

- **C** - Step Scaling doesn't exist for Kinesis.

- **D** - Firehose isn't necessarily faster than Data Streams.

## References

- https://aws.amazon.com/kinesis/data-streams/faqs/
- https://tutorialsdojo.com/amazon-kinesis/

## Domain

Design High-Performing Architectures
