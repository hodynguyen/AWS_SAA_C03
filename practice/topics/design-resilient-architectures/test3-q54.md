# Question 54

## Topic
Design Resilient Architectures

## Question
A Solutions Architect for a global news company is configuring a fleet of EC2 instances in a subnet that currently is in a VPC with an Internet gateway attached. All of these EC2 instances can be accessed from the Internet. The architect launches another subnet and deploys an EC2 instance in it, however, the architect is not able to access the EC2 instance from the Internet.

What could be the possible reasons for this issue? (Select TWO.)

## Options
A. The Amazon EC2 instance does not have an attached Elastic Fabric Adapter (EFA).

B. The Amazon EC2 instance does not have a public IP address associated with it.

C. The route table is not configured properly to send traffic from the EC2 instance to the Internet through the Internet gateway.

D. The Amazon EC2 instance is not a member of the same Auto Scaling group.

E. The route table is not configured properly to send traffic from the EC2 instance to the Internet through the customer gateway (CGW).

## Correct Answers
B, C

## Explanation
Your VPC has an implicit router and you use route tables to control where network traffic is directed. Each subnet in your VPC must be associated with a route table, which controls the routing for the subnet (subnet route table). You can explicitly associate a subnet with a particular route table. Otherwise, the subnet is implicitly associated with the main route table.

A subnet can only be associated with one route table at a time, but you can associate multiple subnets with the same subnet route table. You can optionally associate a route table with an internet gateway or a virtual private gateway (gateway route table). This enables you to specify routing rules for inbound traffic that enters your VPC through the gateway

Be sure that the subnet route table also has a route entry to the internet gateway. If this entry doesn't exist, the instance is in a private subnet and is inaccessible from the internet.

In cases where your EC2 instance cannot be accessed from the Internet (or vice versa), you usually have to check two things:
- Does it have an EIP or public IP address?
- Is the route table properly configured?

Below are the correct answers:
- Amazon EC2 instance does not have a public IP address associated with it.
- The route table is not configured properly to send traffic from the EC2 instance to the Internet through the Internet gateway.

The option that says: The Amazon EC2 instance is not a member of the same Auto Scaling group is incorrect since Auto Scaling Groups do not affect Internet connectivity of EC2 instances.

The option that says: The Amazon EC2 instance doesn't have an attached Elastic Fabric Adapter (EFA) is incorrect because Elastic Fabric Adapter is just a network device that you can attach to your Amazon EC2 instance to accelerate High Performance Computing (HPC) and machine learning applications. EFA enables you to achieve the application performance of an on-premises HPC cluster, with the scalability, flexibility, and elasticity provided by AWS. However, this component is not required in order for your EC2 instance to access the public Internet.

The option that says: The route table is not configured properly to send traffic from the EC2 instance to the Internet through the customer gateway (CGW) is incorrect since CGW is used when you are setting up a VPN. The correct gateway should be an Internet gateway.

## References
- http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Scenario2.html
- https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html
- https://tutorialsdojo.com/amazon-vpc/
