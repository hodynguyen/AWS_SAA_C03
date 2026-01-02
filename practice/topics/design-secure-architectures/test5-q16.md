# Question 16

A company has UAT and production EC2 instances. Employees responsible for UAT should not access production instances.

What is the best way to achieve this?

## Options

A. Launch in different AZs and use MFA.

B. Use AWS RAM to provide permissions.

C. Define tags on servers and add IAM policy condition for specific tags.

D. Launch in separate VPCs with VPC peering.

## Correct Answer

**C. Define tags on servers and add IAM policy condition for specific tags.**

## Explanation

Tag-based access control:
- **Resource tags**: Tag instances as "Environment: UAT" or "Environment: Production"
- **IAM conditions**: Policy allows/denies based on `aws:ResourceTag/Environment`
- **Fine-grained access**: Control access at resource level

### Why other options are incorrect:

- **A, D** - Network separation doesn't prevent IAM-level access if users have permissions.

- **B** - AWS RAM shares resources across accounts, not for restricting within account.

## References

- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policies-for-amazon-ec2.html
- https://tutorialsdojo.com/amazon-ec2/

## Domain

Design Secure Architectures
