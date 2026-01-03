# Question 8

Animation studio uploads 5GB video objects to S3. Uploads take longer than expected.

Which method improves performance?

## Options

A. EBS Provisioned IOPS in LVM stripe configuration.

B. CloudFront with HTTP POST to reduce latency.

C. Enhanced Networking with ENA.

D. S3 Multipart Upload API.

## Correct Answer

**D. S3 Multipart Upload API.**

## Explanation

Multipart Upload benefits:
- **Parallel uploads**: Upload parts simultaneously
- **Improved throughput**: Faster than single upload
- **Retry failed parts**: Don't restart entire upload
- **Recommended**: For objects > 100 MB

### Why other options are incorrect:

- **A** - EBS IOPS helps disk I/O, not S3 uploads.

- **B** - CloudFront is CDN for downloads, not uploads.

- **C** - ENA helps network, but multipart is the key optimization.

## References

- https://docs.aws.amazon.com/AmazonS3/latest/dev/uploadobjusingmpu.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design High-Performing Architectures
