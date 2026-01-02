# Question 12

A company needs a dedicated private connection from VPC to on-premises with high bandwidth and consistent network experience.

Which service should be used?

## Options

A. AWS Direct Connect

B. AWS Site-to-Site VPN

C. Transit Gateway with ECMP

D. Transit VPC

## Correct Answer

**A. AWS Direct Connect**

## Explanation

AWS Direct Connect:
- **Private connection**: Bypasses public Internet
- **Consistent performance**: Dedicated bandwidth
- **Lower latency**: More predictable than Internet
- **High throughput**: Up to 100 Gbps

### Why other options are incorrect:

- **B** - Site-to-Site VPN goes over public Internet, less consistent.

- **C** - Transit Gateway connects VPCs, doesn't provide on-premises connectivity alone.

- **D** - Transit VPC requires VPN or Direct Connect for on-premises connection.

## References

- https://docs.aws.amazon.com/directconnect/latest/UserGuide/Welcome.html
- https://tutorialsdojo.com/aws-direct-connect/

## Domain

Design High-Performing Architectures
