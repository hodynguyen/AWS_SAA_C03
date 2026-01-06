# Question 50

Workload with high sequential read/write to large datasets on local storage.

Which instance type is most suitable?

## Options

A. Compute Optimized.

B. Memory Optimized.

C. Storage Optimized.

D. General Purpose.

## Correct Answer

**C. Storage Optimized.**

## Explanation

Storage Optimized instances:
- **High I/O**: Tens of thousands of IOPS
- **Sequential access**: For large datasets
- **Local storage**: NVMe SSD
- **Use cases**: Data warehousing, log processing

### Why other options are incorrect:

- **A** - Compute for CPU-bound workloads.

- **B** - Memory for in-memory databases.

- **D** - General Purpose balanced, not storage-optimized.

## References

- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/storage-optimized-instances.html
- https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/

## Domain

Design High-Performing Architectures
