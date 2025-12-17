# Question 64

A company wants to host a static website on Amazon S3. The website should be accessible through a custom domain with HTTPS.

Which combination of services should be used? (Select TWO.)

## Options

A. Amazon S3 website hosting with custom SSL certificate.

B. Amazon CloudFront with an ACM certificate.

C. Amazon Route 53 with an alias record.

D. AWS Certificate Manager with S3 directly.

E. Application Load Balancer.

## Correct Answers

**B. Amazon CloudFront with an ACM certificate.**

**C. Amazon Route 53 with an alias record.**

## Explanation

S3 static website hosting doesn't support HTTPS directly. Use CloudFront with an ACM certificate for HTTPS. Route 53 alias records point the custom domain to the CloudFront distribution.

### Why other options are incorrect:

- **A, D** - S3 doesn't support custom SSL certificates directly.

- **E** - ALB is unnecessary for static websites.

## References

- https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Resilient Architectures
