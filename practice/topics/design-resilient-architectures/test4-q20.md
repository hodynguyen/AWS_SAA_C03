# Question 20

A company launched an EC2 instance in a newly created VPC. The instance doesn't have an associated DNS hostname.

What could be the reason?

## Options

A. The newly created VPC has an invalid CIDR block.

B. Amazon Route 53 is not enabled.

C. The DNS resolution and DNS hostname of the VPC configuration should be enabled.

D. The security group of the EC2 instance needs to be modified.

## Correct Answer

**C. The DNS resolution and DNS hostname of the VPC configuration should be enabled.**

## Explanation

In non-default VPCs, DNS hostnames are not automatically assigned. For instances to receive public DNS hostnames, two VPC attributes must be enabled:
- **enableDnsSupport**: Enables DNS resolution within the VPC
- **enableDnsHostnames**: Assigns public DNS hostnames to instances with public IPs

### Why other options are incorrect:

- **A** - Invalid CIDR blocks are rejected during VPC creation. This wouldn't cause DNS hostname issues.

- **B** - Route 53 is a DNS service, but VPC DNS settings control hostname assignment.

- **D** - Security groups filter traffic; they don't affect DNS hostname assignment.

## References

- https://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/vpc-dns.html
- https://tutorialsdojo.com/amazon-vpc/

## Domain

Design Resilient Architectures
