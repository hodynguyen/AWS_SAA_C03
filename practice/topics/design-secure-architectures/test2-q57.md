# Question 57

A company has deployed an application using Amazon EC2 instances with an Application Load Balancer. The security team requires that all inbound traffic to the application be inspected for malicious content.

Which solution provides this capability?

## Options

A. Deploy AWS Shield Standard.

B. Configure Security Groups to filter traffic.

C. Integrate AWS WAF with the Application Load Balancer.

D. Enable VPC Flow Logs.

## Correct Answer

**C. Integrate AWS WAF with the Application Load Balancer.**

## Explanation

AWS WAF is a web application firewall that helps protect web applications from common web exploits. It integrates with ALB to inspect HTTP/HTTPS traffic for malicious content.

### Why other options are incorrect:

- **A** - Shield protects against DDoS, not content inspection.

- **B** - Security Groups filter by IP/port, not content.

- **D** - Flow Logs record traffic metadata, don't inspect content.

## References

- https://aws.amazon.com/waf/
- https://tutorialsdojo.com/aws-waf/

## Domain

Design Secure Architectures
