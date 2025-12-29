# Question 9

A company needs serverless GraphQL APIs with custom domain and HTTPS support for a customer portal.

What solution should be implemented?

## Options

A. AWS Elastic Beanstalk with Route 53 and DNSSEC.

B. VMware Cloud on AWS with Directory Service.

C. EKS Anywhere on Fargate + Outposts with CloudFront Origin Shield.

D. AWS AppSync with custom domain and ACM certificate.

## Correct Answer

**D. AWS AppSync with custom domain and ACM certificate.**

## Explanation

AWS AppSync:
- **Serverless GraphQL**: Fully managed GraphQL service
- **Custom domains**: Built-in custom domain support
- **HTTPS**: Associate ACM certificate for SSL/TLS
- **Real-time**: WebSocket support for subscriptions

### Why other options are incorrect:

- **A** - Elastic Beanstalk runs EC2 instances, not serverless. DNSSEC is for DNS security, not HTTPS.

- **B** - VMware Cloud is for vSphere workloads. Directory Service is for AD, not HTTPS.

- **C** - Outposts is not serverless. Origin Shield is for caching, not HTTPS.

## References

- https://docs.aws.amazon.com/appsync/latest/devguide/custom-domain-name.html
- https://tutorialsdojo.com/aws-appsync/

## Domain

Design High-Performing Architectures
