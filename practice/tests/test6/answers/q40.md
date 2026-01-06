# Question 40

Reserved EC2 instances no longer needed. Need to keep data for audit.

What steps should be taken? (Select TWO.)

## Options

A. Take snapshots and terminate instances.

B. Convert to On-Demand.

C. Stop all instances.

D. Convert to Spot.

E. Sell on Reserved Instance Marketplace.

## Correct Answer

**A. Take snapshots and terminate instances.**

**E. Sell on Reserved Instance Marketplace.**

## Explanation

Decommissioning Reserved Instances:
- **Snapshot data**: Preserve for audit compliance
- **Sell unused RIs**: Recover costs on marketplace
- **Terminate**: Stop paying for instances
- **Third-party sale**: Standard RIs can be sold

### Why other options are incorrect:

- **B** - On-Demand still runs and costs money.

- **C** - Stopped instances still incur storage costs.

- **D** - Converting to Spot doesn't meet the requirement.

## References

- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ri-market-general.html
- https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/

## Domain

Design Cost-Optimized Architectures
