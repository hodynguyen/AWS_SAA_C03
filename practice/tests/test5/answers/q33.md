# Question 33

Multiple Site-to-Site VPN connections have slow connectivity during peak hours.

How to scale VPN throughput?

## Options

A. Increase number of tunnels per VPN.

B. Add secondary customer gateway device.

C. Associate VPCs to ECMP-enabled Transit Gateway with additional VPN tunnels.

D. Add more virtual private gateways to VPC with ECMP.

## Correct Answer

**C. Associate VPCs to ECMP-enabled Transit Gateway with additional VPN tunnels.**

## Explanation

Transit Gateway with ECMP:
- **Equal Cost Multi-Path**: Distributes traffic across tunnels
- **Aggregated throughput**: Multiple 1.25 Gbps tunnels combined
- **Central hub**: Simplifies multi-VPC VPN connectivity

Single VPN tunnel limited to 1.25 Gbps; ECMP scales beyond this.

### Why other options are incorrect:

- **A** - VPN limited to 2 tunnels max, can't increase.

- **B** - Secondary CGW adds redundancy, not throughput.

- **D** - Only one VGW per VPC; no ECMP option on VGW.

## References

- https://aws.amazon.com/blogs/networking-and-content-delivery/scaling-vpn-throughput-using-aws-transit-gateway/
- https://tutorialsdojo.com/aws-transit-gateway/

## Domain

Design High-Performing Architectures
