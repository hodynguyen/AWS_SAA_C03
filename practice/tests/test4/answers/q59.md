# Question 59

A new FTP server should only be accessible from IP address 175.45.116.100. The VPC has default settings.

What is the most suitable security configuration?

## Options

A. NACL rule: UDP, ports 20-21, source 175.45.116.100/0

B. NACL rule: TCP, ports 20-21, source 175.45.116.100/0

C. Security group rule: UDP, ports 20-21, source 175.45.116.100/32

D. Security group rule: TCP, ports 20-21, source 175.45.116.100/32

## Correct Answer

**D. Security group rule: TCP, ports 20-21, source 175.45.116.100/32**

## Explanation

FTP requirements:
- **Protocol**: TCP (not UDP)
- **Ports**: 20 (data) and 21 (control)
- **Source CIDR**: `/32` denotes a single IP; `/0` means entire network
- **Default VPC NACL**: Already allows all traffic, no changes needed

### Why other options are incorrect:

- **A, C** - FTP uses TCP, not UDP.

- **B** - `/0` suffix means entire network (incorrect). Also, default NACL already allows all traffic.

## References

- https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html
- https://tutorialsdojo.com/amazon-vpc/

## Domain

Design Secure Architectures
