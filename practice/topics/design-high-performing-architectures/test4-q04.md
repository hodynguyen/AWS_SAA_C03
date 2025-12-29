# Question 4

A company plans to migrate a NoSQL database to an EC2 instance. The database replicates data automatically for redundancy. The solution needs high IOPS and sequential read/write access.

Which option provides the highest I/O throughput?

## Options

A. Use Memory optimized instances with EBS volume.

B. Use Storage optimized instances with instance store volume.

C. Use Compute optimized instance with instance store volume.

D. Use General purpose instances with EBS volume.

## Correct Answer

**B. Use Storage optimized instances with instance store volume.**

## Explanation

Storage optimized instances (I3, I3en) are designed for workloads requiring high sequential read/write access and low-latency IOPS. They use NVMe SSD instance store volumes, which provide the highest I/O throughput. Since the database already replicates data automatically, the ephemeral nature of instance store is acceptable.

### Why other options are incorrect:

- **A** - Memory optimized instances are for memory-intensive workloads, not high I/O throughput.

- **C** - Compute optimized instances are for CPU-bound applications, not storage-heavy workloads.

- **D** - General purpose instances provide balanced resources but not optimized for high sequential I/O.

## References

- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/storage-optimized-instances.html
- https://tutorialsdojo.com/amazon-ebs/

## Domain

Design High-Performing Architectures
