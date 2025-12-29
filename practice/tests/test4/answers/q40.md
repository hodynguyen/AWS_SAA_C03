# Question 40

A database security group allows MS SQL (port 1433) from 0.0.0.0/0. Only the application tier Auto Scaling group should connect.

Which change follows least privilege best practices?

## Options

A. Change Source to EC2 instance IDs of the Auto Scaling group.

B. Change Source to the Network ACL ID of the application tier.

C. Change Source to the static AnyCast IP address of the application tier.

D. Change Source to the security group ID of the application tier.

## Correct Answer

**D. Change Source to the security group ID of the application tier.**

## Explanation

Security groups can reference other security groups as sources:
- **Dynamic**: Automatically includes all instances in the referenced security group
- **Auto Scaling friendly**: New instances automatically allowed, terminated instances removed
- **Least privilege**: Only application tier instances can access the database

### Why other options are incorrect:

- **A** - Instance IDs change as Auto Scaling adds/removes instances. Requires constant updates.

- **B** - NACLs apply to entire subnets. Can't reference NACL IDs in security groups anyway.

- **C** - AnyCast IPs are for Global Accelerator, not security group configuration.

## References

- https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html
- https://tutorialsdojo.com/amazon-vpc/

## Domain

Design Resilient Architectures
