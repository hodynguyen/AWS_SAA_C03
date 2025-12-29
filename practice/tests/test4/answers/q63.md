# Question 63

An ALB accepts HTTP (port 80) and HTTPS (port 443). All HTTP traffic for a new domain should automatically redirect to HTTPS.

Which ALB configuration satisfies this requirement?

## Options

A. Configure HTTPS listener on 443 to redirect to HTTP on 80.

B. Configure existing HTTP listener to redirect traffic to port 443.

C. Create new HTTP listener on port 80 with redirect to HTTPS on 443.

D. Create new ALB listener on port 443 to redirect HTTP to HTTPS.

## Correct Answer

**B. Configure existing HTTP listener to redirect traffic to port 443.**

## Explanation

ALB supports redirect actions directly on listeners:
- **HTTP listener (port 80)**: Add rule to redirect all traffic to HTTPS (port 443)
- **Status code**: 301 (permanent) or 302 (temporary) redirect
- **No additional resources**: Built-in ALB feature

### Why other options are incorrect:

- **A** - Redirecting HTTPS to HTTP is the opposite of what's needed.

- **C** - Can't create a new listener on port 80 if one already exists.

- **D** - Can't create a new listener on port 443 if one already exists.

## References

- https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-listeners.html
- https://tutorialsdojo.com/aws-elastic-load-balancing-elb/

## Domain

Design Secure Architectures
