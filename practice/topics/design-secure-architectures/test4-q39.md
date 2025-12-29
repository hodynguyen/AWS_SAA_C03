# Question 39

A company has global web applications with custom domain names on ALBs. They need publicly trusted SSL certificates with minimal operational overhead.

What solution meets this requirement?

## Options

A. Launch Let's Encrypt on EC2. Generate certificates with certbot. Associate with ALB.

B. Use ACM Private Certificate Authority. Associate with ALB HTTPS listener.

C. Use OpenSSL self-signed certificates. Import to ACM. Associate with ALB.

D. Use AWS Certificate Manager (ACM) to generate public SSL/TLS certificates. Associate with ALB.

## Correct Answer

**D. Use AWS Certificate Manager (ACM) to generate public SSL/TLS certificates. Associate with ALB.**

## Explanation

ACM public certificates:
- **Free**: No cost for ACM-issued public certificates
- **Auto-renewal**: ACM automatically renews before expiration
- **Easy deployment**: One-click association with ALB, CloudFront, API Gateway
- **Publicly trusted**: Recognized by all major browsers

### Why other options are incorrect:

- **A** - Certificates can't be directly associated with ALB. Must import to ACM first.

- **B** - ACM Private CA issues private certificates, not publicly trusted ones.

- **C** - Self-signed certificates require manual renewal and are not automatically trusted by browsers.

## References

- https://docs.aws.amazon.com/acm/latest/userguide/acm-overview.html
- https://tutorialsdojo.com/aws-certificate-manager/

## Domain

Design Secure Architectures
