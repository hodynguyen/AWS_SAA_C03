# Question 26

A company hosted an e-commerce website on an Auto Scaling group of Amazon EC2 instances behind an Application Load Balancer. The Solutions Architect noticed that the website is receiving a high number of illegitimate external requests from multiple systems with frequently changing IP addresses. To address the performance issues, the Solutions Architect must implement a solution that would block these requests while having minimal impact on legitimate traffic.

Which of the following options fulfills this requirement?

## Options

A. Create a rate-based rule in AWS WAF and associate the web ACL to an Application Load Balancer.

B. Create a custom rule in the security group of the Application Load Balancer to block the offending requests.

C. Create a regular rule in AWS WAF and associate the web ACL to an Application Load Balancer.

D. Create a custom network ACL and associate it with the subnet of the Application Load Balancer to block the offending requests.

## Correct Answer

**A. Create a rate-based rule in AWS WAF and associate the web ACL to an Application Load Balancer.**

## Explanation

AWS WAF is tightly integrated with Amazon CloudFront, the Application Load Balancer (ALB), Amazon API Gateway, and AWS AppSync. A rate-based rule tracks the rate of requests for each originating IP address and triggers the rule action on IPs with rates that go over a limit. You set the limit as the number of requests per 5-minute time span.

You can use this type of rule to put a temporary block on requests from an IP address that's sending excessive requests. When the rule action triggers, AWS WAF applies the action to additional requests from the IP address until the request rate falls below the limit.

### Why other options are incorrect:

- **C** - A regular rule typically matches the statement defined in the rule. If you need to add a rate limit to your rule, you should create a rate-based rule.

- **D** - Although NACLs can help you block incoming traffic, this option wouldn't be able to limit the number of requests from a single IP address that is dynamically changing.

- **B** - Security groups can only allow incoming traffic. You can't deny traffic using security groups. They are also not capable of limiting the rate of traffic.

## References

- https://docs.aws.amazon.com/waf/latest/developerguide/waf-rule-statement-type-rate-based.html
- https://aws.amazon.com/waf/faqs/
- https://tutorialsdojo.com/aws-waf/

## Domain

Design Secure Architectures
