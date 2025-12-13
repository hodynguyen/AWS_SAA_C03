# Question 25

A digital media company shares static content to its premium users around the world and also to their partners who syndicate their media files. The company is looking for ways to reduce its server costs and securely deliver their data to their customers globally with low latency.

Which combination of services should be used to provide the MOST suitable and cost-effective architecture? (Select TWO.)

## Options

A. AWS Lambda

B. Amazon CloudFront

C. AWS Global Accelerator

D. Amazon S3

E. AWS Fargate

## Correct Answers

**B. Amazon CloudFront**

**D. Amazon S3**

## Explanation

Amazon CloudFront is a fast content delivery network (CDN) service that securely delivers data, videos, applications, and APIs globally with low latency and high transfer speeds.

Amazon S3 offers highly durable, scalable, and secure storage. CloudFront integrates with S3 for fast delivery and reduced costs.

### Why other options are incorrect:

- **E** - Fargate is serverless containers, more expensive than S3.

- **A** - Lambda is serverless compute, not for storage or CDN.

- **C** - Global Accelerator is for non-HTTP use cases, not static content.

## References

- https://aws.amazon.com/cloudfront/
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Cost-Optimized Architectures
