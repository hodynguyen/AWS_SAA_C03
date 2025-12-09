# Question 40

A company uses an Application Load Balancer (ALB) for its public-facing multi-tier web applications. The security team has recently reported that there has been a surge of SQL injection attacks lately, which causes critical data discrepancy issues. The same issue is also encountered by its other web applications in other AWS accounts that are behind an ALB. An immediate solution is required to prevent the remote injection of unauthorized SQL queries and protect their applications hosted across multiple accounts.

As a Solutions Architect, what solution would you recommend?

## Options

A. Use AWS WAF and set up a managed rule to block request patterns associated with the exploitation of SQL databases, like SQL injection attacks. Associate it with the Application Load Balancer. Integrate AWS WAF with AWS Firewall Manager to reuse the rules across all the AWS accounts.

B. Use Amazon GuardDuty and set up a managed rule to block request patterns associated with the exploitation of SQL databases.

C. Use Amazon Macie to scan for vulnerabilities and unintended network exposure.

D. Use AWS Network Firewall to filter web vulnerabilities and brute force attacks using stateful rule groups.

## Correct Answer

**A. Use AWS WAF and set up a managed rule to block request patterns associated with the exploitation of SQL databases, like SQL injection attacks. Associate it with the Application Load Balancer. Integrate AWS WAF with AWS Firewall Manager to reuse the rules across all the AWS accounts.**

## Explanation

AWS WAF is a web application firewall that lets you monitor HTTP(S) requests. The AWSManagedRulesSQLiRuleSet contains rules to block request patterns associated with SQL injection attacks.

With AWS Firewall Manager integration, you can centrally define and manage your rules and reuse them across all web applications across multiple accounts.

### Why other options are incorrect:

- **B** - Amazon GuardDuty is a threat detection service and cannot be directly integrated with ALB.

- **D** - AWS Network Firewall is for VPC-level protection, not specifically for ALB or cross-account rule management.

- **C** - Amazon Macie is for data security and privacy, not for blocking SQL injection attacks.

## References

- https://docs.aws.amazon.com/waf/latest/developerguide/how-aws-waf-works.html
- https://docs.aws.amazon.com/waf/latest/developerguide/fms-chapter.html
- https://tutorialsdojo.com/aws-waf

## Domain

Design Secure Architectures
