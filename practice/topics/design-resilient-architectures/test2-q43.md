# Question 43

A company has two On-Demand EC2 instances inside the Virtual Private Cloud in the same Availability Zone but are deployed to different subnets. One EC2 instance is running a database and the other EC2 instance a web application that connects with the database. You need to ensure that these two instances can communicate using their private IP addresses.

What should be done to accomplish this requirement?

## Options

A. Ensure that the default security group allows inbound and outbound traffic.

B. Create a site-to-site VPN connection between the two subnets.

C. Ensure that the route tables have the correct configurations to send traffic from one subnet to another.

D. Enable VPC peering between the subnets.

## Correct Answer

**C. Ensure that the route tables have the correct configurations to send traffic from one subnet to another.**

## Explanation

By default, instances in different subnets within the same VPC can communicate. You need to ensure:
1. Route tables are properly configured
2. Security groups and NACLs allow the traffic

### Why other options are incorrect:

- **D** - VPC peering is between VPCs, not subnets.

- **B** - Site-to-site VPN is for on-premises to AWS.

- **A** - Default SG is not automatically attached.

## References

- https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html
- https://tutorialsdojo.com/amazon-vpc/

## Domain

Design Resilient Architectures
