# Question 8

A company has hundreds of VPCs with VPN connections to data centers across 5 AWS Regions. They need to interconnect all on-premises networks, VPNs, and VPCs into a single gateway with inter-region peering support.

Which solution best meets these requirements?

## Options

A. Set up an AWS Transit Gateway in each region. Route traffic between transit gateways through peering connections.

B. Set up AWS Direct Connect Gateway with a link aggregation group (LAG). Create public virtual interfaces for each Direct Connect connection.

C. Enable inter-region VPC peering between VPCs across regions to keep traffic on AWS backbone.

D. Set up AWS VPN CloudHub for inter-region VPC access and Direct Connect gateway for VPN connections.

## Correct Answer

**A. Set up an AWS Transit Gateway in each region. Route traffic between transit gateways through peering connections.**

## Explanation

Transit Gateway acts as a regional hub connecting VPCs, VPN connections, and Direct Connect gateways. Instead of managing point-to-point connections, all networks connect to the Transit Gateway. For multi-region scenarios, Transit Gateway Peering allows routing between regional Transit Gateways.

### Why other options are incorrect:

- **B** - Direct Connect Gateway only supports private virtual interfaces (not public). LAG is for aggregating bandwidth, not solving interconnectivity.

- **C** - VPC Peering requires manual setup for each pair and doesn't support on-premises connectivity.

- **D** - VPN CloudHub is only for VPN connections, not VPCs. It cannot manage hundreds of VPCs across regions.

## References

- https://aws.amazon.com/transit-gateway/
- https://tutorialsdojo.com/aws-transit-gateway/

## Domain

Design High-Performing Architectures
