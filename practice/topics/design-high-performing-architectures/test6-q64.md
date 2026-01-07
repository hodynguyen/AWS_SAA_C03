# Question 64

Windows EC2 in private subnet with IPv4. Need internet for updates but prevent inbound connections.

Which is highly available?

## Options

A. Egress-Only Internet Gateway.

B. NAT Instance.

C. VPC Endpoint.

D. NAT Gateway.

## Correct Answer

**D. NAT Gateway.**

## Explanation

NAT Gateway for private subnet:
- **IPv4 outbound**: Internet access for updates
- **Prevents inbound**: No internet-initiated connections
- **Highly available**: Managed, redundant
- **Better than NAT Instance**: More bandwidth, managed

### Why other options are incorrect:

- **A** - Egress-only is for IPv6 only.

- **B** - NAT Instance is less HA than NAT Gateway.

- **C** - VPC Endpoint for AWS services, not internet.

## References

- https://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/vpc-nat-gateway.html
- https://tutorialsdojo.com/amazon-vpc/

## Domain

Design High-Performing Architectures
