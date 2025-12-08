# Question 63

A content management system (CMS) is hosted on a fleet of auto-scaled, On-Demand Amazon EC2 instances that use Amazon Aurora as its database. Currently, the system stores the file documents that users upload in one of the attached Amazon EBS volumes. The system's performance has been observed to be slow, and the manager has instructed the team to improve the architecture.

In this scenario, which solution should be implemented to achieve a scalable, highly available, POSIX-compliant shared file system?

## Options

A. Leverage Amazon ElastiCache to cache frequently accessed data and reduce latency

B. Create an Amazon S3 bucket and use this as the storage for the CMS

C. Upgrade your existing EBS volumes to Provisioned IOPS SSD volumes

D. Use Amazon EFS to provide a shared file system for concurrent access to data

## Correct Answer

**D. Use Amazon EFS to provide a shared file system for concurrent access to data**

## Explanation

Amazon EFS provides simple, scalable, elastic file storage. When mounted on EC2 instances, it provides a standard file system interface and access semantics.

Multiple EC2 instances can access an EFS file system at the same time, providing a common data source for workloads running on multiple instances.

### Why other options are incorrect:

- **B** - S3 is object storage, not a file system with POSIX semantics.

- **C** - Upgrading EBS doesn't provide shared storage across multiple instances within an AZ only.

- **A** - ElastiCache improves application performance but is not file storage.

## References

- https://aws.amazon.com/efs/
- https://docs.aws.amazon.com/efs/latest/ug/whatisefs.html
- https://tutorialsdojo.com/amazon-s3-vs-ebs-vs-efs/

## Domain

Design Resilient Architectures
