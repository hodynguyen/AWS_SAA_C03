# Question 19

Web and application tiers need outbound Internet access to fetch data from public APIs but must be inaccessible from the Internet.

Which steps should the Architect implement?

## Options

A. Deploy a NAT gateway in the public subnet and add a route from the private subnet.

B. Deploy a NAT gateway in the private subnet and add a route from the public subnet.

C. Deploy instances to a private subnet and assign Elastic IP addresses.

D. Deploy instances to a public subnet and assign Elastic IP addresses.

## Correct Answer

**A. Deploy a NAT gateway in the public subnet and add a route from the private subnet.**

## Explanation

NAT Gateway enables private subnet instances to access the Internet while remaining unreachable from outside:
1. **NAT Gateway in public subnet**: Has a public IP and route to Internet Gateway
2. **Private subnet route table**: Points 0.0.0.0/0 to the NAT Gateway
3. **Instances stay private**: No direct inbound access from Internet

### Why other options are incorrect:

- **B** - NAT Gateway must be in a public subnet (needs Internet Gateway access).

- **C** - Elastic IPs make instances publicly accessible, violating the requirement.

- **D** - Public subnet instances are directly accessible from the Internet.

## References

- https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html
- https://tutorialsdojo.com/amazon-vpc/

## Domain

Design High-Performing Architectures
