# Question 53

A financial application stores data in S3 in us-east-1. Data must remain available even during AZ outages or regional service failures.

What should the Architect do to ensure data durability?

## Options

A. Create a new S3 bucket in another region and configure Cross-Account Access.

B. Copy the S3 bucket to an EBS-backed EC2 instance.

C. Create a Lifecycle Policy to backup S3 to Glacier.

D. Enable Cross-Region Replication.

## Correct Answer

**D. Enable Cross-Region Replication.**

## Explanation

Cross-Region Replication (CRR):
- **Automatic copying**: Objects replicated to a bucket in another region
- **Regional failure protection**: Data available even if entire region fails
- **Versioning required**: Must be enabled on source and destination

S3 within a single region is already resilient to AZ failures (3+ AZ redundancy).

### Why other options are incorrect:

- **A** - Cross-Account Access doesn't replicate data to another region.

- **B** - EBS is less durable than S3 and tied to a single AZ.

- **C** - Glacier lifecycle archives data but keeps it in the same region.

## References

- https://aws.amazon.com/s3/features/replication/
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Resilient Architectures
