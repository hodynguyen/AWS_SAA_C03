# Question 13

A company is running a multi-tier web application farm in a virtual private cloud (VPC) that is not connected to their corporate network. They are connecting to the VPC over the Internet to manage the fleet of Amazon EC2 instances running in both the public and private subnets. The Solutions Architect has added a bastion host with Microsoft Remote Desktop Protocol (RDP) access to the application instance security groups, but the company wants to further limit administrative access to all of the instances in the VPC.

Which of the following bastion host deployment options will meet this requirement?

## Options

A. Deploy a Windows Bastion host with an Elastic IP address in the public subnet and allow RDP access to bastion only from the corporate IP addresses.

B. Deploy a Windows Bastion host with an Elastic IP address in the public subnet and allow SSH access to the bastion from anywhere.

C. Deploy a Windows Bastion host on the corporate network that has RDP access to all EC2 instances in the VPC.

D. Deploy a Windows Bastion host with an Elastic IP address in the private subnet, and restrict RDP access to the bastion from only the corporate public IP addresses.

## Correct Answer

**A. Deploy a Windows Bastion host with an Elastic IP address in the public subnet and allow RDP access to bastion only from the corporate IP addresses.**

## Explanation

A bastion host is a special purpose computer on a network specifically designed and configured to withstand attacks. It should be in a public subnet with either a public or Elastic IP address with sufficient RDP or SSH access defined in the security group.

### Why other options are incorrect:

- **C** - Bastion host should be in VPC, not corporate network.

- **D** - Should be in public subnet, not private subnet.

- **B** - Windows bastion uses RDP, not SSH.

## References

- https://docs.aws.amazon.com/quickstart/latest/linux-bastion/architecture.html
- https://tutorialsdojo.com/amazon-vpc/

## Domain

Design High-Performing Architectures
