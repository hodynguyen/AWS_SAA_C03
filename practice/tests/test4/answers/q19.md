# Question 19

## Topic
Design High-Performing Architectures

## Question
A Solutions Architect is designing the cloud architecture for the enterprise application suite of the company. Both the web and application tiers need to access the Internet to fetch data from public APIs. However, these servers should be inaccessible from the Internet.

Which of the following steps should the Architect implement to meet the above requirements?

## Options
A. Deploy a NAT gateway in the public subnet and add a route to it from the private subnet where the web and application tiers are hosted.

B. Deploy a NAT gateway in the private subnet and add a route to it from the public subnet where the web and application tiers are hosted.

C. Deploy the web and application tier instances to a private subnet and then allocate an Elastic IP address to each EC2 instance.

D. Deploy the web and application tier instances to a public subnet and then allocate an Elastic IP address to each EC2 instance.

## Correct Answer
A

## Explanation
You can use a network address translation (NAT) gateway to enable instances in a private subnet to connect to the internet or other AWS services but prevent the internet from initiating a connection with those instances. You are charged for creating and using a NAT gateway in your account.

NAT gateway hourly usage and data processing rates apply. Amazon EC2 charges for data transfer also apply. NAT gateways are not supported for IPv6 traffic—use an egress-only internet gateway instead.

To create a NAT gateway, you must specify the public subnet in which the NAT gateway should reside. You must also specify an Elastic IP address to associate with the NAT gateway when you create it. The Elastic IP address cannot be changed once you associate it with the NAT Gateway.

After you've created a NAT gateway, you must update the route table associated with one or more of your private subnets to point Internet-bound traffic to the NAT gateway. This enables instances in your private subnets to communicate with the internet. Each NAT gateway is created in a specific Availability Zone and implemented with redundancy in that zone. You have a limit on the number of NAT gateways you can create in an Availability Zone.

Hence, the correct answer is to deploy a NAT gateway in the public subnet and add a route to it from the private subnet where the web and application tiers are hosted.

Deploying the web and application tier instances to a private subnet and then allocating an Elastic IP address to each EC2 instance is incorrect because an Elastic IP address is just a static, public IPv4 address. In this scenario, you have to use a NAT Gateway instead.

Deploying a NAT gateway in the private subnet and adding a route to it from the public subnet where the web and application tiers are hosted is incorrect because you have to deploy a NAT gateway in the public subnet instead and not on a private one.

Deploying the web and application tier instances to a public subnet and then allocating an Elastic IP address to each EC2 instance is incorrect because having an EIP address is irrelevant as it is only a static, public IPv4 address. Moreover, you should deploy the web and application tier in the private subnet instead of a public subnet to make it inaccessible from the Internet and then just add a NAT Gateway to allow outbound Internet connection.

Reference:

https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html

Check out this Amazon VPC Cheat Sheet:

https://tutorialsdojo.com/amazon-vpc/

Tutorials Dojo's AWS Certified Solutions Architect Associate Exam Study Guide:

https://tutorialsdojo.com/aws-certified-solutions-architect-associate-saa-c03/


