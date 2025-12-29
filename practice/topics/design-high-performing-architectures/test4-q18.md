# Question 18

An HPC cluster uses Provisioned IOPS (io1) volumes for low-latency workloads. The Architect must set optimal IOPS and queue length for 10 GiB volumes.

Which configuration is most suitable?

## Options

A. Set IOPS to 800, maintain low queue length.

B. Set IOPS to 600, maintain high queue length.

C. Set IOPS to 400, maintain low queue length.

D. Set IOPS to 500, maintain low queue length.

## Correct Answer

**D. Set IOPS to 500, maintain low queue length.**

## Explanation

For io1 volumes, the maximum IOPS ratio is 50:1 (IOPS per GiB). A 10 GiB volume supports max 500 IOPS (50 × 10). For transaction-intensive, low-latency workloads:
- **Low queue length**: Reduces latency by avoiding I/O bottlenecks
- **High IOPS**: Maximizes throughput

### Why other options are incorrect:

- **A, B** - 600 and 800 IOPS exceed the 500 IOPS maximum for a 10 GiB volume.

- **C** - 400 IOPS doesn't fully utilize the available capacity. You should use the maximum (500).

## References

- http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSVolumeTypes.html
- https://tutorialsdojo.com/amazon-ebs/

## Domain

Design High-Performing Architectures
