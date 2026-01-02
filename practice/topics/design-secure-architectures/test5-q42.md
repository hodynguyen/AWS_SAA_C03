# Question 42

Web application on EC2 fleet behind ALB in two AZs. Need to add health check configuration.

Which health checks should be implemented?

## Options

A. HTTP or HTTPS health check

B. TCP health check

C. ICMP health check

D. FTP health check

## Correct Answer

**A. HTTP or HTTPS health check**

## Explanation

ALB health checks:
- **HTTP (80)**: Standard web health check
- **HTTPS (443)**: Encrypted health check
- **Application-level**: Validates actual app response
- **Customizable path**: e.g., /health endpoint

### Why other options are incorrect:

- **B** - TCP health check is for NLB/CLB, not ALB.

- **C, D** - ICMP and FTP not supported by any ELB type.

## References

- https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html
- https://tutorialsdojo.com/aws-elastic-load-balancing-elb/

## Domain

Design Secure Architectures
