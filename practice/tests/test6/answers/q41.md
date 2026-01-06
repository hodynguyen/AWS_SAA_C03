# Question 41

EC2 in multiple regions. Need latency-based routing for www.tutorialsdojo.com.

Which option satisfies this?

## Options

A. AWS DataSync.

B. Route 53.

C. Application Load Balancer.

D. Network Load Balancer.

## Correct Answer

**B. Route 53.**

## Explanation

Route 53 latency routing:
- **Multi-region**: Route to lowest latency region
- **DNS-based**: Returns best endpoint IP
- **Health checks**: Skip unhealthy endpoints
- **Auto-updated**: AWS measures latencies

### Why other options are incorrect:

- **A** - DataSync for data transfer, not routing.

- **C, D** - Load balancers work within region only.

## References

- https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html
- https://tutorialsdojo.com/amazon-route-53/

## Domain

Design Resilient Architectures
