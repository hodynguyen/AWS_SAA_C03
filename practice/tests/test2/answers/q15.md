# Question 15

A media company has two VPCs: VPC-1 and VPC-2 with peering connection between each other. VPC-1 only contains private subnets while VPC-2 only contains public subnets. The company uses a single AWS Direct Connect connection and a virtual interface to connect their on-premises network with VPC-1.

Which of the following options increase the fault tolerance of the connection to VPC-1? (Select TWO.)

## Options

A. Establish a hardware VPN over the Internet between VPC-1 and the on-premises network.

B. Establish a new AWS Direct Connect connection and private virtual interface in the same region as VPC-2.

C. Use the AWS VPN CloudHub to create a new AWS Direct Connect connection and private virtual interface in the same region as VPC-2.

D. Establish another AWS Direct Connect connection and private virtual interface in the same AWS region as VPC-1.

E. Establish a hardware VPN over the Internet between VPC-2 and the on-premises network.

## Correct Answers

**A. Establish a hardware VPN over the Internet between VPC-1 and the on-premises network.**

**D. Establish another AWS Direct Connect connection and private virtual interface in the same AWS region as VPC-1.**

## Explanation

VPC peering does not support edge to edge routing. You cannot use VPC-2 to extend the peering relationship to the on-premises network.

To provide fault-tolerant connectivity:
- Establish a hardware VPN over the Internet
- Establish another AWS Direct Connect connection in the same region

### Why other options are incorrect:

- **B, C, E** - VPC peering doesn't allow edge-to-edge routing through VPC-2.

## References

- https://docs.aws.amazon.com/vpc/latest/peering/invalid-peering-configurations.html
- https://tutorialsdojo.com/amazon-vpc/

## Domain

Design Secure Architectures
