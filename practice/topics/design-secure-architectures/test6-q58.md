# Question 58

EC2 in single subnet with IGW. Has public IP but can't connect from internet. Route table shows 10.0.0.0/27 -> local.

What to add?

## Options

A. 10.0.0.0/27 -> Your IGW.

B. 0.0.0.0/27 -> Your IGW.

C. Modify 10.0.0.0/27 -> Your IGW.

D. 0.0.0.0/0 -> Your IGW.

## Correct Answer

**D. 0.0.0.0/0 -> Your IGW.**

## Explanation

Route table for internet access:
- **0.0.0.0/0**: All internet traffic
- **Target IGW**: Route to Internet Gateway
- **Local route**: Keep for VPC internal traffic
- **Public subnet**: Needs route to IGW

### Why other options are incorrect:

- **A** - VPC CIDR shouldn't route to IGW.

- **B** - /27 is not valid for all internet.

- **C** - Local route must stay; add new entry.

## References

- http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Route_Tables.html
- https://tutorialsdojo.com/amazon-vpc/

## Domain

Design Secure Architectures
