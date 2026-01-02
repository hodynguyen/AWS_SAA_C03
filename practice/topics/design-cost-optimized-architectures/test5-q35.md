# Question 35

EC2 in private subnet fetches from S3 via NAT Gateway. How to reduce costs without risking availability?

## Options

A. Remove NAT Gateway and use Gateway VPC endpoint.

B. Replace NAT Gateway with NAT instance on burstable type.

C. Re-assign NAT Gateway to lower EC2 type.

D. Deploy Transit Gateway for S3 peering.

## Correct Answer

**A. Remove NAT Gateway and use Gateway VPC endpoint.**

## Explanation

Gateway VPC Endpoint:
- **Free**: No hourly or data processing charges
- **Highly available**: AWS-managed, redundant
- **Private**: Traffic stays on AWS network
- **S3/DynamoDB only**: Gateway endpoints for these services

### Why other options are incorrect:

- **B** - NAT instance reduces HA/redundancy vs managed NAT Gateway.

- **C** - NAT Gateway is managed service, not an EC2 type to resize.

- **D** - Transit Gateway connects VPCs, doesn't provide S3 access.

## References

- https://docs.aws.amazon.com/vpc/latest/privatelink/vpce-gateway.html
- https://tutorialsdojo.com/amazon-vpc/

## Domain

Design Cost-Optimized Architectures
