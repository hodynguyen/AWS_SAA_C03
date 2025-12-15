# Question 44

A company needs a storage solution that provides very high throughput performance for processing financial workloads. The workloads involve data processing, model training, and simulation. The data is stored in Amazon S3 and must be accessible to the compute resources running on EC2 instances.

Which AWS service should the Solutions Architect recommend?

## Options

A. Amazon EFS with Max I/O performance mode.

B. Amazon FSx for Lustre.

C. AWS DataSync.

D. Amazon S3 File Gateway.

## Correct Answer

**B. Amazon FSx for Lustre.**

## Explanation

Amazon FSx for Lustre is a file system designed for fast processing of workloads such as high-performance computing, video processing, and machine learning. It integrates natively with Amazon S3.

### Why other options are incorrect:

- **A** - EFS is for general-purpose file storage.

- **C** - DataSync is for data transfer, not processing.

- **D** - File Gateway is for on-premises access to S3.

## References

- https://aws.amazon.com/fsx/lustre/
- https://tutorialsdojo.com/amazon-fsx/

## Domain

Design High-Performing Architectures
