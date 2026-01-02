# Question 58

Consolidate access, application, and security logs for real-time analysis. Need to validate heuristics from last 12 hours.

Which is the best approach?

## Options

A. Send logs to SQS, use EC2 ASG to apply heuristics.

B. Configure CloudTrail for custom logs, use EMR for heuristics.

C. Send logs to Kinesis, develop client to apply heuristics.

D. Use EC2 ASG with S3 storage, use EMR for heuristics.

## Correct Answer

**C. Send logs to Kinesis, develop client to apply heuristics.**

## Explanation

Amazon Kinesis:
- **Real-time processing**: Analyze data as it arrives
- **Data retention**: Up to 365 days (24 hours default)
- **Stream consumers**: Custom applications process data
- **Scalable**: Handles any data volume

### Why other options are incorrect:

- **A** - SQS doesn't support real-time streaming analytics.

- **B** - CloudTrail is for API logging, not custom application logs.

- **D** - S3 + EMR is batch processing, not real-time.

## References

- https://aws.amazon.com/kinesis/
- https://tutorialsdojo.com/amazon-kinesis/

## Domain

Design High-Performing Architectures
