# Question 34

A company has a cryptocurrency exchange portal that is hosted in an Auto Scaling group of EC2 instances behind an Application Load Balancer and is deployed across multiple AWS regions. The majority users are from Japan and Sweden. Because of compliance requirements, the Japanese users should connect to the ap-northeast-1 region, while the Swedish users should be connected to the eu-west-1 region.

Which of the following services would allow you to easily fulfill this requirement?

## Options

A. Set up an Application Load Balancers that will automatically route the traffic to the proper AWS region.

B. Use Route 53 Geolocation Routing policy.

C. Set up a new CloudFront web distribution with the geo-restriction feature enabled.

D. Use Route 53 Weighted Routing policy.

## Correct Answer

**B. Use Route 53 Geolocation Routing policy.**

## Explanation

Geolocation routing lets you choose the resources that serve your traffic based on the geographic location of your users. You can localize your content and restrict distribution to specific locations.

### Why other options are incorrect:

- **A** - ALB doesn't route traffic across AWS regions.

- **C** - CloudFront geo-restriction is for blocking, not routing.

- **D** - Weighted routing is for proportional distribution.

## References

- https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html
- https://tutorialsdojo.com/amazon-route-53/

## Domain

Design High-Performing Architectures
