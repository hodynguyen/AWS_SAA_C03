# Question 25

## Topic
Design Resilient Architectures

## Question
An aerospace engineering company recently adopted a hybrid cloud infrastructure with AWS. One of the responsibilities of the Solutions Architect is to launch an Amazon VPC with both public and private subnets for Amazon EC2 instances and database instances. The architecture must ensure each subnet is properly defined within the assigned VPC CIDR block.

Which of the following statements are true regarding VPC subnets? (Select TWO.)

## Options
A. Each subnet spans 2 Availability Zones.

B. Each newly created subnet is, by default, linked to the main route table of the VPC.

C. EC2 instances in a private subnet can communicate with the Internet only if they have an Elastic IP.

D. Each subnet maps to a single Availability Zone.

E. The allowed block size in VPC is between a /16 netmask (65,536 IP addresses) and /27 netmask (32 IP addresses).

## Correct Answers
**B. Each newly created subnet is, by default, linked to the main route table of the VPC.**

**D. Each subnet maps to a single Availability Zone.**

## Explanation
A VPC spans all the Availability Zones in the region. After creating a VPC, you can add one or more subnets in each Availability Zone. When you create a subnet, you specify the CIDR block for the subnet, which is a subset of the VPC CIDR block. Each subnet must reside entirely within one Availability Zone and cannot span zones.

**Why other options are incorrect:**
- **Option A** is incorrect because each subnet must reside only within one Availability Zone.
- **Option C** is incorrect because EC2 instances can communicate via NAT Gateway/Instance, not just Elastic IP.
- **Option E** is incorrect because the allowed block size is between /16 and /28 (16 IP addresses), not /27.

## References
- https://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Subnets.html
- https://docs.aws.amazon.com/vpc/latest/userguide/vpc-ip-addressing.html
- https://tutorialsdojo.com/amazon-vpc/
