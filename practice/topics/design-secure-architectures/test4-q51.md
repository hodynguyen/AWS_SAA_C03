# Question 51

A company needs to distribute training videos stored in S3 via CloudFront. The content should not be publicly accessible from S3 directly.

What method should be used?

## Options

A. Create an IAM user for CloudFront and grant S3 access.

B. Create an S3 bucket policy listing CloudFront distribution ID as principal.

C. Create an Origin Access Control (OAC) and grant S3 access to it.

D. Create a WAF web ACL to block public S3 access.

## Correct Answer

**C. Create an Origin Access Control (OAC) and grant S3 access to it.**

## Explanation

Origin Access Control (OAC):
- **CloudFront-only access**: S3 bucket policy grants access only to CloudFront's OAC
- **Blocks direct S3 access**: Users must go through CloudFront
- **Supports SSE-KMS**: Works with KMS-encrypted objects

Update the S3 bucket policy to allow the OAC principal.

### Why other options are incorrect:

- **A** - You can't create an IAM user for CloudFront distributions.

- **B** - CloudFront distribution ID can't be used as a principal directly.

- **D** - WAF protects against attacks, not for controlling S3 access.

## References

- https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html
- https://tutorialsdojo.com/amazon-cloudfront/

## Domain

Design Secure Architectures
