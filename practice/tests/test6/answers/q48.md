# Question 48

HPC cluster needs scalable file system. POSIX interface, works with S3.

Which is MOST suitable?

## Options

A. Amazon EBS.

B. Amazon FSx for Windows.

C. Amazon EFS.

D. Amazon FSx for Lustre.

## Correct Answer

**D. Amazon FSx for Lustre.**

## Explanation

FSx for Lustre for HPC:
- **High performance**: Sub-millisecond latency
- **S3 integration**: Native, transparent
- **POSIX-compliant**: Standard file interface
- **HPC optimized**: ML, video, EDA workloads

### Why other options are incorrect:

- **A** - EBS is block storage, single-instance.

- **B** - FSx Windows for Windows apps, not HPC.

- **C** - EFS doesn't natively work with S3.

## References

- https://aws.amazon.com/fsx/lustre/
- https://tutorialsdojo.com/amazon-fsx/

## Domain

Design High-Performing Architectures
