# Question 27

A mobile game uses API Gateway and DynamoDB with preconfigured read/write capacity. During peak loads, DynamoDB throttles requests causing slow performance.

How can you improve performance?

## Options

A. Integrate an Application Load Balancer with DynamoDB.

B. Use DynamoDB Auto Scaling.

C. Add the DynamoDB table to an Auto Scaling Group.

D. Create an SQS queue in front of DynamoDB.

## Correct Answer

**B. Use DynamoDB Auto Scaling.**

## Explanation

DynamoDB Auto Scaling uses Application Auto Scaling to dynamically adjust provisioned throughput based on traffic patterns:
- **Increases capacity** during traffic spikes to prevent throttling
- **Decreases capacity** during low traffic to reduce costs

No code changes required—configure target utilization and min/max capacity.

### Why other options are incorrect:

- **A** - ALB is for HTTP traffic to compute targets, not DynamoDB.

- **C** - Auto Scaling Groups are for EC2 instances, not DynamoDB tables.

- **D** - SQS buffers requests but doesn't increase DynamoDB throughput.

## References

- https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/AutoScaling.html
- https://tutorialsdojo.com/amazon-dynamodb/

## Domain

Design High-Performing Architectures
