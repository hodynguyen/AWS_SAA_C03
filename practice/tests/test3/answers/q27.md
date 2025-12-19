# Question 27

## Topic
Design Secure Architectures

## Question
A Solutions Architect is unable to connect to the newly deployed EC2 instance via SSH using a home computer. However, the Architect was able to successfully access other existing instances in the VPC without any issues.

Which of the following should the Architect check and possibly correct to restore connectivity?

## Options
A. Use Amazon Data Lifecycle Manager.

B. Configure the Network Access Control List of your VPC to permit ingress traffic over port 22 from your IP.

C. Configure the Security Group of the EC2 instance to permit ingress traffic over port 3389 from your IP.

D. Configure the Security Group of the EC2 instance to permit ingress traffic over port 22 from your IP.

## Correct Answer
D

## Explanation
When connecting to your EC2 instance via SSH, you need to ensure that port 22 is allowed on the security group of your EC2 instance.

A security group acts as a virtual firewall that controls the traffic for one or more instances. You add rules to each security group that allow traffic to or from its associated instances.

**Why other options are incorrect:**
- **Option A** is incorrect because Data Lifecycle Manager manages EBS snapshot lifecycles, not network access.
- **Option B** is incorrect because since other instances work, the NACL is not the issue; the problem is with the instance's security group.
- **Option C** is incorrect because port 3389 is for RDP (Windows), not SSH.

## References
- http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html
- https://tutorialsdojo.com/comparison-of-aws-services/
