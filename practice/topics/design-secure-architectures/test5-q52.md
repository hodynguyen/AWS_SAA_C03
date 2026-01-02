# Question 52

Multi-region application must block a specific country per government policy.

Which is the recommended action?

## Options

A. Update NACLs on EC2 subnets to deny country IPs.

B. Create WAF web ACL with geo match to block country. Associate with ALBs.

C. Update NACLs on ALB subnets to deny country IPs.

D. Use Network Firewall with domain list rule to block country.

## Correct Answer

**B. Create WAF web ACL with geo match to block country. Associate with ALBs.**

## Explanation

AWS WAF geo-blocking:
- **Country-level blocking**: Geo match rule statement
- **ALB integration**: Associate web ACL with ALBs
- **Easy management**: Single rule for all country IPs
- **Automatic updates**: AWS maintains country-to-IP mappings

### Why other options are incorrect:

- **A, C** - NACLs require listing all IPs; impractical for countries.

- **D** - Domain list rules block domains, not countries.

## References

- https://docs.aws.amazon.com/waf/latest/developerguide/waf-rule-statement-type-geo-match.html
- https://tutorialsdojo.com/aws-waf/

## Domain

Design Secure Architectures
