# Question 9

A Solutions Architect identified a series of DDoS attacks while monitoring the Amazon VPC. The Architect needs to fortify the current cloud infrastructure to protect the data of the clients.

Which of the following is the most suitable solution to mitigate these kinds of attacks?

## Options

A. Set up a web application firewall using AWS WAF to filter, monitor, and block HTTP traffic.

B. Using the AWS Firewall Manager, set up a security layer that will prevent SYN floods, UDP reflection attacks, and other DDoS attacks.

C. Use AWS Shield Advanced to detect and mitigate DDoS attacks.

D. A combination of Security Groups and Network Access Control Lists to only allow authorized traffic to access your VPC.

## Correct Answer

**C. Use AWS Shield Advanced to detect and mitigate DDoS attacks.**

## Explanation

For higher levels of protection against attacks targeting your applications running on Amazon EC2, ELB, Amazon CloudFront, and Amazon Route 53 resources, you can subscribe to AWS Shield Advanced. In addition to the network and transport layer protections that come with Standard, AWS Shield Advanced provides additional detection and mitigation against large and sophisticated DDoS attacks, near real-time visibility into attacks, and integration with AWS WAF.

AWS Shield Advanced also gives you 24x7 access to the AWS DDoS Response Team (DRT) and protection against DDoS related spikes in your EC2, ELB, CloudFront, and Route 53 charges.

### Why other options are incorrect:

- **B** - AWS Firewall Manager is mainly used to simplify your AWS WAF administration and maintenance tasks across multiple accounts and resources. It does not protect your VPC against DDoS attacks.

- **A** - Even though AWS WAF can help you block common attack patterns like SQL injection or cross-site scripting, this is still not enough to withstand DDoS attacks.

- **D** - Although using a combination of Security Groups and NACLs are valid to provide security to your VPC, this is not enough to mitigate a DDoS attack.

## References

- https://d1.awsstatic.com/whitepapers/Security/DDoS_White_Paper.pdf
- https://aws.amazon.com/shield/
- https://tutorialsdojo.com/aws-shield/

## Domain

Design Secure Architectures
