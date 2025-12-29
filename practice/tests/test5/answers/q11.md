# Question 11

A web application will receive over 2000 PUT and 3500 GET requests per second to S3 at peak hour.

What should be done to ensure optimal performance?

## Options

A. Use predictable naming with sequential numbers or dates.

B. Do nothing. S3 automatically manages performance at this scale.

C. Use Byte-Range Fetches for multiple ranges per GET request.

D. Add random prefix to key names.

## Correct Answer

**B. Do nothing. S3 automatically manages performance at this scale.**

## Explanation

S3 automatically scales:
- **3,500 PUT/second per prefix**: Built-in support
- **5,500 GET/second per prefix**: Built-in support
- **No manual tuning**: AWS manages partitions automatically

The workload (2000 PUT, 3500 GET) is well within S3's automatic limits.

### Why other options are incorrect:

- **A** - Sequential naming can cause hot partitions, but S3 handles this automatically now.

- **C** - Byte-Range Fetches are one range per request, not multiple.

- **D** - Random prefixes no longer needed since S3's 2018 performance update.

## References

- https://docs.aws.amazon.com/AmazonS3/latest/dev/request-rate-perf-considerations.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design High-Performing Architectures
