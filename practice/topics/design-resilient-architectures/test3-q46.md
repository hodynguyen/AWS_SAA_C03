# Question 46

## Topic
Design Resilient Architectures

## Question
A large insurance company has an AWS account that contains three VPCs (DEV, UAT and PROD) in the same region. UAT is peered to both PROD and DEV using a VPC peering connection. All VPCs have non-overlapping CIDR blocks. The company wants to push minor code releases from Dev to Prod to speed up time to market.

Which of the following options helps the company accomplish this?

## Options
A. Do nothing. Since these two VPCs are already connected via UAT, they already have a connection to each other.

B. Change the DEV and PROD VPCs to have overlapping CIDR blocks to be able to connect them.

C. Create a new entry to PROD in the DEV route table using the VPC peering connection as the target.

D. Create a new VPC peering connection between PROD and DEV with the appropriate routes.

## Correct Answer
D

## Explanation
A VPC peering connection is a networking connection between two VPCs that enables you to route traffic between them privately. You can create a VPC peering connection between your own VPCs, with a VPC in another AWS account, or with a VPC in a different AWS Region.

VPC peering does not support transitive peering relationships. Even though UAT is peered to both PROD and DEV, DEV and PROD cannot communicate through UAT. You need to create a direct VPC peering connection between PROD and DEV.

**Why other options are incorrect:**
- **Option A** is incorrect because VPC peering is not transitive.
- **Option B** is incorrect because overlapping CIDR blocks would prevent VPC peering.
- **Option C** is incorrect because you need to create the VPC peering connection first before adding routes.

## References
- https://docs.aws.amazon.com/vpc/latest/peering/what-is-vpc-peering.html
- https://tutorialsdojo.com/amazon-vpc/
