# Question 3

A global company has deployed numerous AWS Outposts servers in various remote locations worldwide. These servers frequently need to download software updates consisting of multiple files from an S3 bucket in the us-west-2 region. The company is experiencing significant delays in distributing these updates across all servers.

What solution would most effectively reduce the deployment latency while minimizing operational overhead?

## Options

A. Create an Amazon CloudFront distribution with the us-west-2 S3 bucket as the origin. Use signed URLs for software downloads.

B. Use Amazon S3 Transfer Acceleration on the existing S3 bucket and have the Outposts servers use the Transfer Acceleration endpoint for downloads.

C. Set up AWS Global Accelerator to route traffic from Outposts servers to the nearest AWS edge location, then use private VIF connections to access the S3 bucket in us-west-2.

D. Set up an Amazon CloudFront distribution with the us-west-2 S3 bucket as the primary origin and create a secondary origin in another region, implementing a CachingDisabled cache policy. Use signed URLs for downloads.

## Correct Answer

**A. Create an Amazon CloudFront distribution with the us-west-2 S3 bucket as the origin. Use signed URLs for software downloads.**

## Explanation

Amazon CloudFront utilizes a global network of edge locations to cache content closer to end users, enhancing performance and reducing the load on origin servers.

By combining CloudFront with the S3 bucket, the application benefits from:
- Global content delivery through edge locations
- Caching capabilities for frequently downloaded files
- Signed URLs for security
- Reduced data transfer costs

### Why other options are incorrect:

- **B** - S3 Transfer Acceleration doesn't provide caching.

- **C** - Global Accelerator doesn't integrate directly with S3 for downloads.

- **D** - CachingDisabled policy negates CloudFront's benefits.

## References

- https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/GettingStarted.SimpleDistribution.html
- https://tutorialsdojo.com/amazon-cloudfront/

## Domain

Design Resilient Architectures
