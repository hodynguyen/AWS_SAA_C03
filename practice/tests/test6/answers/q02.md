# Question 2

HPC system with ECS tasks needs shared storage for high-frequency read/write. Output 10MB per task, total <10TB.

Which is the MOST suitable solution?

## Options

A. EFS with Provisioned Throughput and Max I/O performance mode.

B. FSx for Windows File Server with SMB.

C. EFS with Bursting Throughput and General Purpose mode.

D. DynamoDB with DAX as container mount point.

## Correct Answer

**A. EFS with Provisioned Throughput and Max I/O performance mode.**

## Explanation

EFS for HPC:
- **Provisioned Throughput**: Consistent high throughput regardless of storage size
- **Max I/O mode**: Optimized for high-frequency parallel access
- **ECS integration**: Mount as container volume
- **POSIX-compliant**: Works with Linux containers

### Why other options are incorrect:

- **B** - FSx Windows not optimal for Linux ECS containers.

- **C** - Bursting won't sustain constant high-frequency access.

- **D** - DynamoDB is a database, not a mountable file system.

## References

- https://docs.aws.amazon.com/AmazonECS/latest/developerguide/tutorial-efs-volumes.html
- https://tutorialsdojo.com/amazon-efs/

## Domain

Design High-Performing Architectures
