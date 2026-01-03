# Question 4

HPC data analytics needs POSIX-compliant storage, multi-AZ redundancy, thousands of concurrent EC2 connections.

Which storage service is most suitable?

## Options

A. Amazon ElastiCache

B. Amazon EFS

C. Amazon EBS Volumes

D. Amazon S3

## Correct Answer

**B. Amazon EFS**

## Explanation

Amazon EFS:
- **POSIX-compliant**: Full file system semantics
- **Multi-AZ**: Redundant across AZs by default
- **Concurrent access**: Thousands of EC2 instances simultaneously
- **Elastic scaling**: Grows/shrinks automatically

### Why other options are incorrect:

- **A** - ElastiCache is in-memory caching, not file storage.

- **C** - EBS is single-instance block storage.

- **D** - S3 is object storage, not POSIX-compliant.

## References

- https://docs.aws.amazon.com/efs/latest/ug/performance.html
- https://tutorialsdojo.com/amazon-efs/

## Domain

Design High-Performing Architectures
