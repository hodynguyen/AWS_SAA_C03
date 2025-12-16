# Question 49

A company requires that all HTTP traffic to its web applications be automatically redirected to HTTPS. The application runs behind an Application Load Balancer.

Which solution meets this requirement with minimal operational effort?

## Options

A. Configure an AWS WAF web ACL to check for HTTP traffic and redirect to HTTPS.

B. Configure a Lambda function to inspect incoming requests.

C. Configure a listener rule on the ALB to redirect HTTP traffic to HTTPS.

D. Configure Amazon CloudFront to handle the redirect.

## Correct Answer

**C. Configure a listener rule on the ALB to redirect HTTP traffic to HTTPS.**

## Explanation

ALB supports redirect actions natively. You can configure an HTTP listener with a rule that redirects to HTTPS without any additional resources.

### Why other options are incorrect:

- **A** - WAF inspects requests but isn't ideal for redirects.

- **B** - Lambda adds unnecessary complexity.

- **D** - CloudFront is additional unless already in use.

## References

- https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-listeners.html
- https://tutorialsdojo.com/aws-elastic-load-balancing-elb/

## Domain

Design Secure Architectures
