# Question 35

Online banking with EC2. Scalable, cost-effective distributed system.

Which solution is most suitable?

## Options

A. EC2 + ELB + SNS as message buffer.

B. ASG + SQS with scaling trigger on queue size.

C. On-Demand EC2 + SQS.

D. EC2 + ALB + Step Functions.

## Correct Answer

**B. ASG + SQS with scaling trigger on queue size.**

## Explanation

Distributed system with scaling:
- **Auto Scaling**: Scale based on demand
- **SQS queue**: Decouple components
- **Queue-based scaling**: Scale on queue depth
- **Cost-effective**: Only run needed capacity

### Why other options are incorrect:

- **A** - SNS is pub/sub, not message buffer.

- **C** - On-Demand is expensive; no auto-scaling.

- **D** - Step Functions for workflows, not message buffering.

## References

- https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-using-sqs-queue.html
- https://tutorialsdojo.com/aws-auto-scaling/

## Domain

Design High-Performing Architectures
