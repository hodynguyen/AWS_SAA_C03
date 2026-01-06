# Question 39

Track GPS coordinates from trucks every 5 seconds. Real-time processing from multiple consumers.

Which AWS service for this?

## Options

A. Amazon EMR.

B. Amazon Kinesis.

C. Amazon AppStream.

D. Amazon SQS.

## Correct Answer

**B. Amazon Kinesis.**

## Explanation

Amazon Kinesis:
- **Real-time streaming**: Process as data arrives
- **Multiple consumers**: Fan-out capability
- **High frequency**: Handle data every 5 seconds
- **Scalable**: Handle any volume

### Why other options are incorrect:

- **A** - EMR for batch processing, not real-time.

- **C** - AppStream for desktop streaming, not data.

- **D** - SQS has latency; not optimized for real-time.

## References

- https://aws.amazon.com/kinesis/
- https://tutorialsdojo.com/amazon-kinesis/

## Domain

Design High-Performing Architectures
