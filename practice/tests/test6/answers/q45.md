# Question 45

ALB with EC2 ASG. Route /api/android to Android-Target-Group, /api/ios to iOS-Target-Group.

How to implement this?

## Options

A. Use path conditions with ALB.

B. Replace with NLB and use host conditions.

C. Replace with Gateway Load Balancer.

D. Use host conditions with ALB.

## Correct Answer

**A. Use path conditions with ALB.**

## Explanation

ALB path-based routing:
- **Path conditions**: Route based on URL path
- **/api/android**: To Android target group
- **/api/ios**: To iOS target group
- **Pattern matching**: Supports wildcards

### Why other options are incorrect:

- **B** - NLB doesn't support path-based routing.

- **C** - Gateway LB doesn't support path routing.

- **D** - Host conditions route by hostname, not path.

## References

- https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-listeners.html
- https://tutorialsdojo.com/aws-elastic-load-balancing-elb/

## Domain

Design High-Performing Architectures
