# Question 20

EC2 instances in private subnet process sensitive data and deliver to S3. The data should not pass through public Internet.

How should this be designed?

## Options

A. Create Internet gateway in public subnet with route to S3.

B. Configure Transit Gateway with route to S3.

C. Provision NAT gateway in private subnet with route to S3.

D. Configure VPC Endpoint with route to S3.

## Correct Answer

**D. Configure VPC Endpoint with route to S3.**

## Explanation

VPC Gateway Endpoint for S3:
- **Private connectivity**: Traffic stays on AWS network
- **No Internet exposure**: Doesn't traverse public Internet
- **Free**: No hourly charges for Gateway endpoints
- **Route table integration**: Add S3 prefix list to route table

### Why other options are incorrect:

- **A** - Internet Gateway routes traffic through public Internet.

- **B** - Transit Gateway connects VPCs, doesn't provide S3 access.

- **C** - NAT Gateway routes through Internet (and goes in public subnet, not private).

## References

- https://docs.aws.amazon.com/vpc/latest/userguide/vpc-endpoints.html
- https://tutorialsdojo.com/amazon-vpc/

## Domain

Design Secure Architectures
