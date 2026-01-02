# Question 39

ALB with two target groups. Port 80 is allowed in security group, but instances show "out of service."

What could be the root cause?

## Options

A. Wrong subnet was used.

B. Wrong AMI was used.

C. Health check configuration is not properly defined.

D. Wrong instance type was used.

## Correct Answer

**C. Health check configuration is not properly defined.**

## Explanation

Common health check issues:
- **Wrong path**: Health check URL returns error
- **Wrong port**: Health check on wrong port
- **Timeout**: Health check times out before response
- **Wrong status code**: App returns unexpected HTTP status

### Why other options are incorrect:

- **A, B, D** - These would cause instance issues, but wouldn't specifically cause "out of service" in load balancer without affecting security group access.

## References

- http://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-healthchecks.html
- https://tutorialsdojo.com/aws-elastic-load-balancing-elb/

## Domain

Design High-Performing Architectures
