# Question 6

An organization requires a persistent block storage volume to support its mission-critical workloads. The backup data will be stored in an object storage service and, after 30 days, transitioned to an archival storage service for long-term retention.

What should be done to meet the above requirement?

## Options

A. Attach an instance store volume in your Amazon EC2 instance. Use Amazon S3 to store your backup data and configure a lifecycle policy to transition your objects to S3 One Zone-IA.

B. Attach an Amazon EBS volume in your Amazon EC2 instance. Use Amazon S3 to store your backup data and configure a lifecycle policy to transition your objects to S3 Glacier Flexible Retrieval.

C. Attach an instance store volume in your existing Amazon EC2 instance. Use Amazon S3 to store your backup data and configure a lifecycle policy to transition your objects to S3 Glacier Flexible Retrieval.

D. Attach an Amazon EBS volume in your Amazon EC2 instance. Use Amazon S3 to store your backup data and configure a lifecycle policy to transition your objects to S3 One Zone-IA.

## Correct Answer

**B. Attach an Amazon EBS volume in your Amazon EC2 instance. Use Amazon S3 to store your backup data and configure a lifecycle policy to transition your objects to S3 Glacier Flexible Retrieval.**

## Explanation

Amazon Elastic Block Store (EBS) is an easy-to-use, high-performance block storage service designed for use with Amazon Elastic Compute Cloud (EC2) for both throughput and transaction-intensive workloads at any scale.

In this scenario, three services are required:
1. **Amazon EBS** - for persistent block storage for mission-critical workloads
2. **Amazon S3** - object storage service to store backup data
3. **Amazon S3 Glacier Flexible Retrieval** - archive storage for long-term retention

### Why other options are incorrect:

- **D** - S3 One Zone-IA is an infrequently accessed storage class, not a storage class for data archiving.

- **C** - Instance Store volume is temporary block-level storage. You can't attach instance store volumes to an instance after you've launched it.

- **A** - Instance store volume is not suitable for mission-critical workloads because data can be lost if the underlying disk drive fails. S3 Glacier Flexible Retrieval is more suitable for archival than S3 One Zone-IA.

## References

- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonEBS.html
- https://aws.amazon.com/s3/storage-classes/
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Resilient Architectures
