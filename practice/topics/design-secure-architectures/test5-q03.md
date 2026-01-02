# Question 3

A company deploys an application on EC2 with NLB. The security team needs to inspect traffic entering and exiting the VPC.

Which approach satisfies the requirements?

## Options

A. Enable Traffic Mirroring on NLB. Create traffic mirror filter.

B. Use Network Access Analyzer. Create Network Access Scope.

C. Create firewall using AWS Network Firewall at VPC level with custom rule groups.

D. Create firewall at subnet level using Amazon Detective. Use VPC Reachability Analyzer.

## Correct Answer

**C. Create firewall using AWS Network Firewall at VPC level with custom rule groups.**

## Explanation

AWS Network Firewall:
- **Stateful inspection**: Deep packet inspection for ingress/egress
- **VPC-level deployment**: Filters traffic at VPC perimeter
- **Custom rules**: Define allow/deny rules based on IPs, protocols, domains
- **Suricata-based**: Uses open-source IPS for intrusion detection

### Why other options are incorrect:

- **A** - Traffic Mirroring copies traffic for analysis but doesn't filter/block it.

- **B** - Network Access Analyzer reports on access, doesn't perform inspection.

- **D** - Detective is for security investigation; Reachability Analyzer tests connectivity.

## References

- https://docs.aws.amazon.com/network-firewall/latest/developerguide/what-is-aws-network-firewall.html
- https://tutorialsdojo.com/aws-network-firewall/

## Domain

Design Secure Architectures
