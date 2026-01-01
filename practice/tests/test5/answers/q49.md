# Question 49

Web application behind ALB needs geo-blocking but should allow specific IPs from blocked country.

Which combination should be implemented? (Select TWO.)

## Options

A. Create ALB listener rule for approved IPs.

B. Create WAF web ACL with IP Set rule for approved IPs.

C. Use Transit Gateway with NACLs for geo-blocking.

D. Set up geo match in ALB.

E. Add WAF rule with geo match to block specific country.

## Correct Answer

**B. Create WAF web ACL with IP Set rule for approved IPs.**

**E. Add WAF rule with geo match to block specific country.**

## Explanation

AWS WAF geo-blocking with exceptions:
1. **Geo match rule**: Block requests from specific country
2. **IP Set rule**: Allow specific IPs (higher priority)
3. **Rule order**: Allow rule evaluated first, then block

### Why other options are incorrect:

- **A** - ALB listener rules can't filter by country.

- **C** - Transit Gateway/NACLs can't do geo-blocking.

- **D** - ALB doesn't have geo match capability.

## References

- https://docs.aws.amazon.com/waf/latest/developerguide/classic-web-acl-geo-conditions.html
- https://tutorialsdojo.com/aws-waf/

## Domain

Design Secure Architectures
