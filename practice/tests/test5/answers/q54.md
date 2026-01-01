# Question 54

EC2 instances under SSH brute force attack. IP addresses identified. Need quickest fix while setting up WAF/GuardDuty/Shield.

Which provides the quickest way to stop attacks?

## Options

A. Place instances in private subnets.

B. Assign static Anycast IP addresses.

C. Block IP addresses in Network ACL.

D. Remove Internet Gateway from VPC.

## Correct Answer

**C. Block IP addresses in Network ACL.**

## Explanation

NACL for quick blocking:
- **Immediate effect**: Changes apply instantly
- **IP-based blocking**: Add deny rules for attacker IPs
- **Stateless**: Simple deny rule blocks all traffic from IP
- **Minimal disruption**: Doesn't affect legitimate traffic

### Why other options are incorrect:

- **A** - Moving to private subnets makes instances inaccessible to you too.

- **B** - Anycast IPs are for Global Accelerator, not security.

- **D** - Removing IGW cuts all Internet access.

## References

- https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html
- https://tutorialsdojo.com/security-group-vs-nacl/

## Domain

Design Secure Architectures
