# Question 51

A company needs to implement a solution that provides persistent storage for a Docker container environment running on Amazon ECS. The containers are running on EC2 instances and need to share files between tasks.

Which storage option is most appropriate?

## Options

A. Amazon EBS volumes.

B. Amazon S3.

C. Amazon EFS.

D. EC2 instance store.

## Correct Answer

**C. Amazon EFS.**

## Explanation

Amazon EFS provides a simple, scalable, elastic file system for Linux-based workloads. It can be shared across multiple ECS tasks and is ideal for container environments needing persistent shared storage.

### Why other options are incorrect:

- **A** - EBS can only attach to one instance at a time.

- **B** - S3 is object storage, not file system storage.

- **D** - Instance store is ephemeral and local.

## References

- https://aws.amazon.com/efs/
- https://tutorialsdojo.com/amazon-efs/

## Domain

Design Resilient Architectures
