# Question 20

Medical images in S3 behind CloudFront. New uploads must keep previous versions.

Which is the most suitable solution?

## Options

A. Custom cache behavior with Minimum TTL of 0.

B. Use versioned objects.

C. Invalidate files in CloudFront.

D. Add Cache-Control no-cache to S3 bucket.

## Correct Answer

**B. Use versioned objects.**

## Explanation

S3 versioning with CloudFront:
- **Object versioning**: Different URLs for each version
- **No overwriting**: Old versions always accessible
- **Less expensive**: Than invalidation
- **Access logs**: Include version in filename

### Why other options are incorrect:

- **A** - Cache TTL doesn't prevent overwriting.

- **C** - Invalidation costs money; still overwrites.

- **D** - Cache-Control affects caching, not versioning.

## References

- https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/UpdatingExistingObjects.html
- https://tutorialsdojo.com/amazon-cloudfront/

## Domain

Design Resilient Architectures
