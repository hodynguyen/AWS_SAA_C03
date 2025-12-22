# Question 52

## Topic
Design Cost-Optimized Architectures

## Question
A company is hosting an application on EC2 instances that regularly pushes and fetches data in Amazon S3. Due to a change in compliance, the instances need to be moved on a private subnet. Along with this change, the company wants to lower the data transfer costs by configuring its AWS resources.

How can this be accomplished in the MOST cost-efficient manner?

## Options
A. Set up a NAT Gateway in the public subnet to connect to Amazon S3.

B. Set up an AWS Transit Gateway to access Amazon S3.

C. Create an Amazon S3 gateway endpoint to enable a connection between the instances and Amazon S3.

D. Create an Amazon S3 interface endpoint to enable a connection between the instances and Amazon S3.

## Correct Answer
C

## Explanation
VPC endpoints for Amazon S3 simplify access to S3 from within a VPC by providing configurable and highly reliable secure connections to S3 that do not require an internet gateway or Network Address Translation (NAT) device. When you create an S3 VPC endpoint, you can attach an endpoint policy to it that controls access to Amazon S3.

You can use two types of VPC endpoints to access Amazon S3: gateway endpoints and interface endpoints. A gateway endpoint is a gateway that you specify in your route table to access Amazon S3 from your VPC over the AWS network. Interface endpoints extend the functionality of gateway endpoints by using private IP addresses to route requests to Amazon S3 from within your VPC, on-premises, or from a different AWS Region. Interface endpoints are compatible with gateway endpoints. If you have an existing gateway endpoint in the VPC, you can use both types of endpoints in the same VPC.

There is no additional charge for using gateway endpoints. However, standard charges for data transfer and resource usage still apply.

Hence, the correct answer is: Create an Amazon S3 gateway endpoint to enable a connection between the instances and Amazon S3.

The option that says: Set up a NAT Gateway in the public subnet to connect to Amazon S3 is incorrect. This will enable a connection between the private EC2 instances and Amazon S3 but it is not the most cost-efficient solution. NAT Gateways are charged on an hourly basis even for idle time.

The option that says: Create an Amazon S3 interface endpoint to enable a connection between the instances and Amazon S3 is incorrect. This is also a possible solution but it's not the most cost-effective solution. You pay an hourly rate for every provisioned Interface endpoint.

The option that says: Set up an AWS Transit Gateway to access Amazon S3 is incorrect because this service is mainly used for connecting VPCs and on-premises networks through a central hub.

## References
- https://docs.aws.amazon.com/AmazonS3/latest/userguide/privatelink-interface-endpoints.html
- https://docs.aws.amazon.com/vpc/latest/privatelink/vpce-gateway.html
- https://tutorialsdojo.com/amazon-s3/
