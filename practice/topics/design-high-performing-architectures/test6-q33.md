# Question 33

CloudFront with EC2 origin for dynamic content. Need high availability.

Which option provides HA?

## Options

A. S3 for dynamic content in origin group.

B. Auto Scaling group as origin group.

C. Two EC2 in different AZs as origin group.

D. Lambda@Edge in origin group.

## Correct Answer

**C. Two EC2 in different AZs as origin group.**

## Explanation

CloudFront origin failover:
- **Origin group**: Primary + secondary origin
- **Two EC2s**: In different AZs for HA
- **Automatic failover**: If primary fails
- **HTTP status codes**: Trigger failover

### Why other options are incorrect:

- **A** - S3 can't serve dynamic content.

- **B** - ASG isn't directly usable as origin group.

- **D** - Lambda@Edge for edge computing, not origin.

## References

- https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/high_availability_origin_failover.html
- https://tutorialsdojo.com/amazon-cloudfront/

## Domain

Design High-Performing Architectures
