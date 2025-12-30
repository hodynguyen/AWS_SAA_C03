# Question 22

NACL allows all inbound, denies all outbound. Security group allows inbound SSH from any IP, no outbound rules.

What changes are needed to allow SSH connection?

## Options

A. Modify outbound security group to allow outbound traffic.

B. No action needed. Already accessible via SSH.

C. Modify both outbound security group and NACL.

D. Modify NACL to allow outbound traffic.

## Correct Answer

**D. Modify NACL to allow outbound traffic.**

## Explanation

Key difference:
- **Security groups are stateful**: Inbound rule auto-allows return traffic
- **NACLs are stateless**: Need explicit inbound AND outbound rules

SSH needs outbound NACL rule for response traffic. Security group's stateful nature handles return traffic automatically.

### Why other options are incorrect:

- **A** - Security group is stateful; outbound rule not needed.

- **B** - NACL blocks outbound, so SSH responses can't leave.

- **C** - Only NACL needs modification, not security group.

## References

- https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html
- https://tutorialsdojo.com/amazon-vpc/

## Domain

Design Secure Architectures
