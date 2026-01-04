# Question 19

HR VPC and Finance VPC in different regions need connectivity. IPS for traffic inspection required.

Which architecture should be set up?

## Options

A. Transit Gateway + AWS Network Firewall.

B. Route 53 Traffic Policy + DNS Firewall.

C. Direct Connect Gateway + Security Hub.

D. NAT Gateway + Systems Manager.

## Correct Answer

**A. Transit Gateway + AWS Network Firewall.**

## Explanation

Transit Gateway + Network Firewall:
- **Transit Gateway**: Connects VPCs across regions
- **Network Firewall**: IPS for traffic inspection
- **Stateful inspection**: Block vulnerability exploits
- **Managed**: Both are fully managed services

### Why other options are incorrect:

- **B** - Traffic Policy for routing; DNS Firewall for DNS only.

- **C** - Direct Connect for on-premises; Security Hub for posture.

- **D** - NAT for internet access; Session Manager for SSH.

## References

- https://aws.amazon.com/transit-gateway
- https://aws.amazon.com/network-firewall

## Domain

Design Resilient Architectures
