# Question 56

A company is running a legacy application that uses a file-based storage system. The application needs to migrate to AWS with minimal code changes. The storage must be accessible from multiple EC2 instances simultaneously.

Which storage solution should be used?

## Options

A. Amazon S3 with S3 File Gateway.

B. Amazon EBS with Multi-Attach.

C. Amazon EFS.

D. AWS Storage Gateway Volume Gateway.

## Correct Answer

**C. Amazon EFS.**

## Explanation

Amazon EFS provides a POSIX-compliant file system that can be mounted by multiple EC2 instances simultaneously. It requires minimal code changes for file-based applications.

### Why other options are incorrect:

- **A** - File Gateway adds latency for direct mount.

- **B** - EBS Multi-Attach is limited to io1/io2 and specific use cases.

- **D** - Volume Gateway is for on-premises use.

## References

- https://aws.amazon.com/efs/
- https://tutorialsdojo.com/amazon-efs/

## Domain

Design Resilient Architectures
