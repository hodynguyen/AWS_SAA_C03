# Question 27

EC2 instances in two custom VPCs (Ohio and N.Virginia) need to transfer data without traversing the public Internet.

Which combination achieves this? (Select TWO.)

## Options

A. Deploy VPC endpoint in each region.

B. Re-configure route table target and destination.

C. Launch NAT Gateway in public subnet of each VPC.

D. Create Egress-only Internet Gateway.

E. Set up VPC peering connection.

## Correct Answer

**B. Re-configure route table target and destination.**

**E. Set up VPC peering connection.**

## Explanation

Inter-region VPC Peering:
- **Private connectivity**: Traffic stays on AWS backbone
- **Cross-region support**: Works between regions
- **Route table update**: Point subnets to peering connection
- **No Internet exposure**: Never traverses public Internet

### Why other options are incorrect:

- **A** - VPC endpoints are regional, don't support inter-region connectivity.

- **C** - NAT Gateway routes to Internet, not private connectivity.

- **D** - Egress-only IGW is for IPv6 Internet access, not VPC connectivity.

## References

- https://docs.aws.amazon.com/vpc/latest/peering/what-is-vpc-peering.html
- https://tutorialsdojo.com/amazon-vpc/

## Domain

Design Secure Architectures
