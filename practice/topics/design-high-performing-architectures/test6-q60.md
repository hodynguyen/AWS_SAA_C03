# Question 60

Gaming servers on Fargate. TCP Layer 4 load balancing, millions of requests, ultra-low latency.

Which solution?

## Options

A. Network Load Balancer.

B. Application Load Balancer.

C. Route 53 Weighted Routing.

D. Custom Fargate microservice as LB.

## Correct Answer

**A. Network Load Balancer.**

## Explanation

NLB for gaming:
- **Layer 4**: TCP/UDP load balancing
- **Millions of requests**: Per second capacity
- **Ultra-low latency**: Optimized for performance
- **Fargate compatible**: Works with containers

### Why other options are incorrect:

- **B** - ALB is Layer 7; can't do TCP.

- **C** - Route 53 can't handle millions with ultra-low latency.

- **D** - NLB works with Fargate; custom LB unnecessary.

## References

- https://aws.amazon.com/elasticloadbalancing/features/#compare
- https://tutorialsdojo.com/aws-elastic-load-balancing-elb/

## Domain

Design High-Performing Architectures
