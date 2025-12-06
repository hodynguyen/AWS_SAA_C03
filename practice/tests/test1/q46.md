# Question 46

A company needs to deploy at least two Amazon EC2 instances to support the normal workloads of its application and automatically scale up to six EC2 instances to handle the peak load. The architecture must be highly available and fault-tolerant as it is processing mission-critical workloads.

As a Solutions Architect, what should be done to meet this requirement?

## Options

A. Create an Auto Scaling group of EC2 instances and set the minimum capacity to 2 and the maximum capacity to 6. Use 2 Availability Zones and deploy 1 instance for each AZ.

B. Create an Auto Scaling group of EC2 instances and set the minimum capacity to 2 and the maximum capacity to 4. Deploy 2 instances in Availability Zone A and 2 instances in Availability Zone B.

C. Create an Auto Scaling group of EC2 instances and set the minimum capacity to 4 and the maximum capacity to 6. Deploy 2 instances in Availability Zone A and another 2 instances in Availability Zone B.

D. Create an Auto Scaling group of EC2 instances and set the minimum capacity to 2 and the maximum capacity to 6. Deploy 4 instances in Availability Zone A.

## Correct Answer

**C. Create an Auto Scaling group of EC2 instances and set the minimum capacity to 4 and the maximum capacity to 6. Deploy 2 instances in Availability Zone A and another 2 instances in Availability Zone B.**

## Explanation

For fault tolerance, you need redundant resources. Since the requirement is at least 2 instances running at all times, you need 4 instances minimum (2 in each AZ). If an AZ fails, you still have 2 instances running in the other AZ.

Setting minimum capacity to 4 ensures that even during an AZ outage, at least 2 instances remain available.

### Why other options are incorrect:

- **D** - Deploying in a single AZ doesn't protect against datacenter/AZ failures.

- **A** - With only 1 instance per AZ, an AZ outage leaves only 1 instance (below the 2-instance requirement).

- **B** - The maximum capacity of 4 doesn't meet the requirement of scaling up to 6 instances.

## References

- https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html
- https://docs.aws.amazon.com/documentdb/latest/developerguide/regions-and-azs.html
- https://tutorialsdojo.com/aws-auto-scaling/

## Domain

Design Resilient Architectures
