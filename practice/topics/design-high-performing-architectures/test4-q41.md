# Question 41

A company needs to process real-time streaming data of globally distributed users for clickstream analysis. The solution must process data close to users with low latency.

What is the most suitable solution?

## Options

A. CloudFront + Lambda@Edge for processing. Kinesis for streaming. Store in S3.

B. CloudFront + Lambda@Edge for processing. Athena for streaming. Store in S3.

C. CloudFront + Route 53 Geoproximity routing. Kinesis for streaming. Store in S3.

D. CloudFront + Route 53 latency-based routing. Kinesis for streaming. Store in S3.

## Correct Answer

**A. CloudFront + Lambda@Edge for processing. Kinesis for streaming. Store in S3.**

## Explanation

Lambda@Edge executes code at CloudFront edge locations:
- **Geographic proximity**: Code runs near users for low latency
- **Real-time processing**: Process requests/responses at edge
- **Kinesis integration**: Stream clickstream data to Kinesis for real-time analytics

### Why other options are incorrect:

- **B** - Athena is for ad-hoc SQL queries on S3, not real-time streaming.

- **C, D** - Route 53 only routes traffic; it can't process data or run code at the edge.

## References

- https://aws.amazon.com/lambda/edge/
- https://tutorialsdojo.com/aws-lambda/

## Domain

Design High-Performing Architectures
