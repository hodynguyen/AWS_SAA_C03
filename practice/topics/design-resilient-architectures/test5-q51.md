# Question 51

Web servers behind ALB with Route 53. How to configure zone apex to point to ALB?

## Options

A. Create CNAME record pointing to ALB DNS name.

B. Create alias for CNAME record to ALB.

C. Create A record pointing to ALB IP address.

D. Create A record aliased to ALB DNS name.

## Correct Answer

**D. Create A record aliased to ALB DNS name.**

## Explanation

Route 53 Alias records:
- **Zone apex support**: CNAME can't be used at apex (e.g., example.com)
- **ALB integration**: Points to ALB DNS name
- **Dynamic IP handling**: ALB IPs can change; alias handles this
- **Free queries**: No charge for alias queries to AWS resources

### Why other options are incorrect:

- **A, B** - CNAME can't be created for zone apex.

- **C** - ALB IP addresses change; A record would break.

## References

- https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resource-record-sets-choosing-alias-non-alias.html
- https://tutorialsdojo.com/amazon-route-53/

## Domain

Design Resilient Architectures
