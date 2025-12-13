# Question 27

A company has a dynamic web app written in MEAN stack that is going to be launched in the next month. There is a probability that the traffic will be quite high in the first couple of weeks. In the event of a load failure, how can you set up DNS failover to a static website?

## Options

A. Add more servers in case the application fails.

B. Enable failover to an application hosted in an on-premises data center.

C. Duplicate the exact application architecture in another region and configure DNS weight-based routing.

D. Use Route 53 with the failover option to a static S3 website bucket or CloudFront distribution.

## Correct Answer

**D. Use Route 53 with the failover option to a static S3 website bucket or CloudFront distribution.**

## Explanation

You can create a new Route 53 with the failover option to a static S3 website bucket or CloudFront distribution as an alternative.

This provides a cost-effective failover solution without duplicating the entire application infrastructure.

### Why other options are incorrect:

- **C** - Duplicating entire architecture is not cost-effective.

- **B** - Not maximizing AWS environment like Route 53 failover.

- **A** - Adding servers during failure causes downtime.

## References

- https://aws.amazon.com/premiumsupport/knowledge-center/fail-over-s3-r53/
- https://tutorialsdojo.com/amazon-route-53/

## Domain

Design Resilient Architectures
