# Question 59

## Topic
Design Secure Architectures

## Question
A startup launched a new FTP server using an On-Demand EC2 instance in a newly created VPC with default settings. The server should not be accessible publicly but only through the IP address 175.45.116.100 and nowhere else.

Which of the following is the most suitable way to implement this requirement?

## Options
A. Create a new Network ACL inbound rule in the subnet of the EC2 instance with the following details:

B. Protocol: UDP

C. Port Range: 20 - 21

D. Source: 175.45.116.100/0

E. Allow/Deny: ALLOW

F. Create a new Network ACL inbound rule in the subnet of the EC2 instance with the following details:

G. Protocol: TCP

H. Port Range: 20 - 21

I. Source: 175.45.116.100/0

J. Allow/Deny: ALLOW

K. Create a new inbound rule in the security group of the EC2 instance with the following details:

L. Protocol: UDP

M. Port Range: 20 - 21

N. Source: 175.45.116.100/32

O. Create a new inbound rule in the security group of the EC2 instance with the following details:

P. Protocol: TCP

Q. Port Range: 20 - 21

R. Source: 175.45.116.100/32

## Correct Answer
O

## Explanation
The FTP protocol uses TCP via ports 20 and 21. This should be configured in your security groups or in your Network ACL inbound rules. As required by the scenario, you should only allow the individual IP of the client and not the entire network. Therefore, in the Source, the proper CIDR notation should be used. The /32 denotes one IP address and the /0 refers to the entire network.

It is stated in the scenario that you launched the EC2 instances in a newly created VPC with default settings. Your VPC automatically comes with a modifiable default network ACL. By default, it allows all inbound and outbound IPv4 traffic and, if applicable, IPv6 traffic. Hence, you actually don't need to explicitly add inbound rules to your Network ACL to allow inbound traffic, if your VPC has a default setting.

The below option is incorrect:

Create a new inbound rule in the security group of the EC2 instance with the following details:

Protocol: UDP

Port Range: 20 - 21

Source: 175.45.116.100/32

Although the configuration of the Security Group is valid, the provided Protocol is incorrect. Take note that FTP uses TCP and not UDP.

The below option is also incorrect:

Create a new Network ACL inbound rule in the subnet of the EC2 instance with the following details:

Protocol: TCP

Port Range: 20 - 21

Source: 175.45.116.100/0

Allow/Deny: ALLOW

Although setting up an inbound Network ACL is valid, the source is invalid since it must be an IPv4 or IPv6 CIDR block. In the provided IP address, the /0 refers to the entire network and not a specific IP address. In addition, it is stated in the scenario that the newly created VPC has default settings and by default, the Network ACL allows all traffic. This means that there is actually no need to configure your Network ACL.

Likewise, the below option is also incorrect:

Create a new Network ACL inbound rule in the subnet of the EC2 instance with the following details:

Protocol: UDP

Port Range: 20 - 21

Source: 175.45.116.100/0

Allow/Deny: ALLOW

Just like in the above, the source is also invalid. Take note that FTP uses TCP and not UDP, which is one of the reasons why this option is wrong. In addition, it is stated in the scenario that the newly created VPC has default settings and by default, the Network ACL allows all traffic. This means that there is actually no need to configure your Network ACL.

References:

https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html

https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html

Check out this Amazon VPC Cheat Sheet:

https://tutorialsdojo.com/amazon-vpc/


