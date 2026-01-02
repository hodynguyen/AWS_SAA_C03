# Question 26

Microservices send messages to SQS; backend EC2 processes them. The company has an SLA for response time, but I/O-intensive operations and growing messages cause missed SLAs.

Which solution improves processing time?

## Options

A. ASG with target tracking on CPUUtilization at 80%.

B. Launch EC2 to cluster placement group.

C. Replace with larger instance size.

D. ASG with target tracking on ApproximateAgeOfOldestMessage.

## Correct Answer

**D. ASG with target tracking on ApproximateAgeOfOldestMessage.**

## Explanation

ApproximateAgeOfOldestMessage metric:
- **Time-sensitive**: Scales based on how long messages wait
- **SLA-focused**: Directly addresses response time requirements
- **Proactive scaling**: More instances when queue ages

### Why other options are incorrect:

- **A** - CPU-based scaling doesn't consider message age for SLA.

- **B** - Placement groups improve network, not processing capacity.

- **C** - Single larger instance doesn't scale dynamically with load.

## References

- https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-using-sqs-queue.html
- https://tutorialsdojo.com/amazon-sqs/

## Domain

Design High-Performing Architectures
