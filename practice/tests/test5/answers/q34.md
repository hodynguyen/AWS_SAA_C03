# Question 34

Route 53 is used instead of ELB to distribute traffic. You want specific percentage of traffic to each of two EC2 instances.

Which routing policy should be used?

## Options

A. Latency

B. Failover

C. Geolocation

D. Weighted

## Correct Answer

**D. Weighted**

## Explanation

Weighted routing:
- **Percentage-based**: Assign weights to records
- **Traffic splitting**: e.g., weight 1 vs 255 = 1/256 vs 255/256
- **Flexible**: Adjust weights anytime
- **Use cases**: Load balancing, A/B testing, migrations

### Why other options are incorrect:

- **A** - Latency routes to lowest latency region, not percentage.

- **B** - Failover is active/passive, not weighted.

- **C** - Geolocation routes by user location, not percentage.

## References

- http://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html
- https://tutorialsdojo.com/amazon-route-53/

## Domain

Design High-Performing Architectures
