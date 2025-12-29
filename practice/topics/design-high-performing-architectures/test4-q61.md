# Question 61

A global news website hosted on EC2 has slow response times due to increased load, affecting revenue.

Which services can solve this problem cost-effectively? (Select TWO.)

## Options

A. Use AWS Storage Gateway for content distribution.

B. Deploy website to all regions in different VPCs.

C. Use Amazon RDS Multi-AZ for read scalability.

D. Use Amazon ElastiCache for in-memory caching.

E. Use Amazon CloudFront with website as custom origin.

## Correct Answer

**D. Use Amazon ElastiCache for in-memory caching.**

**E. Use Amazon CloudFront with website as custom origin.**

## Explanation

For global content delivery and reduced latency:
- **CloudFront**: CDN caches content at edge locations worldwide
- **ElastiCache**: In-memory cache reduces database/backend load

Together they reduce origin server load and deliver content from locations closest to users.

### Why other options are incorrect:

- **A** - Storage Gateway is for hybrid cloud storage, not content delivery.

- **B** - Multi-region deployment is expensive and complex.

- **C** - Multi-AZ provides HA, not read scalability or latency improvement.

## References

- https://aws.amazon.com/elasticache/
- https://tutorialsdojo.com/amazon-cloudfront/

## Domain

Design High-Performing Architectures
