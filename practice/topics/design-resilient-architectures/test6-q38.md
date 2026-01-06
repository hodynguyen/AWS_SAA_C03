# Question 38

EC2 with IPv6 in private subnet. Need internet access but prevent inbound IPv6 traffic.

Which VPC feature allows this?

## Options

A. NAT instances.

B. Egress-only Internet gateway.

C. Internet Gateway.

D. NAT Gateway.

## Correct Answer

**B. Egress-only Internet gateway.**

## Explanation

Egress-only IGW:
- **IPv6 only**: For IPv6 outbound traffic
- **Prevents inbound**: No internet-initiated connections
- **Private subnet**: Allows outbound internet access
- **Highly available**: Redundant and scalable

### Why other options are incorrect:

- **A, D** - NAT for IPv4; can't block inbound IPv6.

- **C** - IGW allows both inbound and outbound.

## References

- https://docs.aws.amazon.com/vpc/latest/userguide/egress-only-internet-gateway.html
- https://tutorialsdojo.com/amazon-vpc/

## Domain

Design Resilient Architectures
