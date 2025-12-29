# Question 57

You have a third-party SSL/TLS certificate for your web application behind an ALB.

Where can you safely import this certificate? (Select TWO.)

## Options

A. AWS Certificate Manager

B. IAM certificate store

C. A private S3 bucket with versioning enabled

D. An S3 bucket with SSE-C encryption

E. CloudFront

## Correct Answer

**A. AWS Certificate Manager**

**B. IAM certificate store**

## Explanation

For third-party certificates on AWS:
- **ACM**: Preferred method, supports auto-renewal reminders, easy ALB/CloudFront integration
- **IAM certificate store**: Alternative for regions where ACM is not available

Both allow association with ALB, CloudFront, and other AWS services.

### Why other options are incorrect:

- **C, D** - S3 is not designed for certificate storage/deployment.

- **E** - CloudFront uses certificates but can't store them for other services.

## References

- https://docs.aws.amazon.com/acm/latest/userguide/import-certificate.html
- https://tutorialsdojo.com/aws-certificate-manager/

## Domain

Design Cost-Optimized Architectures
