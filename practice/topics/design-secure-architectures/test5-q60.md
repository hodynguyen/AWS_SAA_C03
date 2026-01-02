# Question 60

Startup with on-premises AD and 10 computers needs virtual desktops in VPC connected to on-premises.

Which AWS services should be used?

## Options

A. Directory Services, VPN, S3

B. Directory Services, VPN, WorkSpaces

C. Directory Services, VPN, IAM

D. Directory Services, VPN, ClassicLink

## Correct Answer

**B. Directory Services, VPN, WorkSpaces**

## Explanation

Solution components:
- **AWS Directory Service**: Integrate with on-premises AD
- **VPN connection**: Connect VPC to on-premises network
- **Amazon WorkSpaces**: Managed virtual desktops in VPC

### Why other options are incorrect:

- **A** - S3 is storage, not virtual desktops.

- **C** - IAM is for AWS access control, not virtual desktops.

- **D** - ClassicLink is deprecated; connects EC2-Classic to VPC.

## References

- https://aws.amazon.com/workspaces/
- https://tutorialsdojo.com/amazon-workspaces/

## Domain

Design Secure Architectures
