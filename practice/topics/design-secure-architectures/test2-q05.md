# Question 5

A company is hosting its web application in an Auto Scaling group of EC2 instances behind an Application Load Balancer. Recently, the Solutions Architect identified a series of SQL injection attempts and cross-site scripting attacks to the application, which had adversely affected their production data.

Which of the following should the Architect implement to mitigate this kind of attack?

## Options

A. Using AWS Firewall Manager, set up security rules that block SQL injection and cross-site scripting attacks. Associate the rules to the Application Load Balancer.

B. Use Amazon GuardDuty to prevent any further SQL injection and cross-site scripting attacks in your application.

C. Block all the IP addresses where the SQL injection and cross-site scripting attacks originated using the Network Access Control List.

D. Set up security rules that block SQL injection and cross-site scripting attacks in AWS Web Application Firewall (WAF). Associate the rules to the Application Load Balancer.

## Correct Answer

**D. Set up security rules that block SQL injection and cross-site scripting attacks in AWS Web Application Firewall (WAF). Associate the rules to the Application Load Balancer.**

## Explanation

AWS WAF is a web application firewall that lets you monitor HTTP and HTTPS requests forwarded to Amazon API Gateway, CloudFront, or an Application Load Balancer. AWS WAF lets you control access to your content based on conditions you specify.

AWS WAF lets you choose behaviors like:
- Allow all requests except specified ones
- Block all requests except specified ones
- Count requests matching certain properties

### Why other options are incorrect:

- **B** - GuardDuty is for threat detection, not prevention.

- **A** - Firewall Manager simplifies WAF administration but doesn't replace it.

- **C** - NACLs are not effective against SQL injection and XSS attacks.

## References

- https://aws.amazon.com/waf/
- https://tutorialsdojo.com/aws-waf/

## Domain

Design Secure Architectures
