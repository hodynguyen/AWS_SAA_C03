# Question 52

A startup has 5 TB of S3 data to share with a European partner. They need to minimize data transfer costs and disable anonymous access.

Which solution is most cost-effective?

## Options

A. Enable cross-account access to allow partner downloads.

B. Enable Requester Pays feature on the S3 bucket.

C. Enable S3 Object Lock in governance mode.

D. Enable Cross-Region Replication to partner's bucket.

## Correct Answer

**B. Enable Requester Pays feature on the S3 bucket.**

## Explanation

Requester Pays buckets:
- **Requester pays transfer costs**: The partner (requester) pays for data download
- **Disables anonymous access**: All requesters must authenticate
- **No additional configuration**: Simple setting change

### Why other options are incorrect:

- **A** - Cross-account access doesn't shift transfer costs to the partner.

- **C** - Object Lock prevents deletion, doesn't affect transfer costs.

- **D** - CRR incurs transfer costs from source to destination (paid by you).

## References

- https://docs.aws.amazon.com/AmazonS3/latest/userguide/RequesterPaysBuckets.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Secure Architectures
