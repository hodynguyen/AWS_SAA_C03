# Question 31

An AI-powered Forex trading application consumes thousands of data sets to train its machine learning model. The application's workload requires a high-performance, parallel hot storage to process the training datasets concurrently. It also needs cost-effective cold storage to archive those datasets that yield low profit.

Which of the following Amazon storage services should the developer use?

## Options

A. Use Amazon FSx For Lustre and Amazon S3 for hot and cold storage respectively.

B. Use Amazon Elastic File System and Amazon S3 for hot and cold storage respectively.

C. Use Amazon FSx For Windows File Server and Amazon S3 for hot and cold storage respectively.

D. Use Amazon FSx For Lustre and the Provisioned IOPS SSD (io1) volumes of Amazon EBS for hot and cold storage respectively.

## Correct Answer

**A. Use Amazon FSx For Lustre and Amazon S3 for hot and cold storage respectively.**

## Explanation

Hot storage refers to the storage that keeps frequently accessed data. Cold storage refers to the storage that keeps rarely accessed data. In terms of pricing, the colder the data, the cheaper it is to store, and the costlier it is to access when needed.

Amazon FSx For Lustre is a high-performance file system for fast processing of workloads. Lustre is a popular open-source parallel file system which stores data across multiple network file servers to maximize performance and reduce bottlenecks.

The question has two requirements:
1. High-performance, parallel hot storage to process the training datasets concurrently.
2. Cost-effective cold storage to keep the archived datasets that are accessed infrequently

Amazon FSx For Lustre provides a high-performance, parallel file system for hot data. Amazon S3 supports cold storage via Amazon S3 Glacier / Glacier Deep Archive.

### Why other options are incorrect:

- **D** - Provisioned IOPS SSD (io1) volumes are designed for hot data used in I/O-intensive workloads. EBS Cold HDD is much more expensive than Amazon S3 Glacier.

- **B** - Although EFS supports concurrent access to data, it does not have the high-performance ability typically required for machine learning workloads.

- **C** - Amazon FSx For Windows File Server does not have a parallel file system, unlike Lustre.

## References

- https://aws.amazon.com/fsx/
- https://docs.aws.amazon.com/whitepapers/latest/cost-optimization-storage-optimization/aws-storage-services.html
- https://tutorialsdojo.com/amazon-fsx/

## Domain

Design High-Performing Architectures
