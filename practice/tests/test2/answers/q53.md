# Question 53

A Solutions Architect is designing a solution for a company that runs batch processing jobs. The jobs can be interrupted and restarted without any impact on the final output. The company wants to minimize compute costs.

Which EC2 purchasing option is most cost-effective?

## Options

A. On-Demand Instances.

B. Reserved Instances.

C. Spot Instances.

D. Dedicated Hosts.

## Correct Answer

**C. Spot Instances.**

## Explanation

Spot Instances are available at up to a 90% discount compared to On-Demand prices. They are ideal for fault-tolerant, flexible workloads like batch processing that can handle interruptions.

### Why other options are incorrect:

- **A** - On-Demand is more expensive.

- **B** - Reserved Instances require commitment.

- **D** - Dedicated Hosts are for licensing/compliance.

## References

- https://aws.amazon.com/ec2/spot/
- https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/

## Domain

Design Cost-Optimized Architectures
