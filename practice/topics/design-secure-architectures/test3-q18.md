# Question 18

## Topic
Design Secure Architectures

## Question
A large financial firm needs to set up a Linux bastion host to allow access to the Amazon EC2 instances running in their VPC. For security purposes, only the clients connecting from the corporate external public IP address 175.45.116.100 should have SSH access to the host.

Which is the best option that can meet the customer's requirement?

## Options
A. Network ACL Inbound Rule: Protocol – TCP, Port Range-22, Source 175.45.116.100/0

B. Network ACL Inbound Rule: Protocol – UDP, Port Range – 22, Source 175.45.116.100/32

C. Security Group Inbound Rule: Protocol – TCP. Port Range – 22, Source 175.45.116.100/32

D. Security Group Inbound Rule: Protocol – UDP, Port Range – 22, Source 175.45.116.100/32

## Correct Answer
C

## Explanation
A bastion host is a special purpose computer on a network specifically designed and configured to withstand attacks. When setting up a bastion host in AWS, you should only allow the individual IP of the client and not the entire network.

The /32 denotes one IP address, and the /0 refers to the entire network. SSH uses TCP protocol on port 22.

**Why other options are incorrect:**
- **Option A** is incorrect because /0 allows the entire network, not just the specific IP.
- **Option B** is incorrect because SSH uses TCP, not UDP.
- **Option D** is incorrect because SSH uses TCP, not UDP.

## References
- http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html
- https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/
