# Question 56

You need to analyze AWS costs. Which of the following incurs charges? (Select TWO.)

## Options

A. Using an Amazon VPC

B. A stopped On-Demand EC2 Instance

C. EBS Volumes attached to stopped EC2 Instances

D. Public Data Set

E. A running EC2 Instance

## Correct Answer

**C. EBS Volumes attached to stopped EC2 Instances**

**E. A running EC2 Instance**

## Explanation

AWS billing:
- **Running EC2**: Charged per second/hour based on instance type
- **EBS volumes**: Charged for provisioned storage regardless of EC2 state
- **Stopped EC2**: No compute charges, but EBS storage still billed

### Why other options are incorrect:

- **A** - VPC itself is free. You only pay for NAT Gateways, VPN connections, etc.

- **B** - Stopped instances don't incur compute charges (but EBS does).

- **D** - Public data sets are stored at no charge.

## References

- https://aws.amazon.com/ec2/pricing/
- https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/

## Domain

Design Cost-Optimized Architectures
