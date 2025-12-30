# Question 18

1000 Linux servers in multiple AZs need simultaneous access to storage using NFSv4. Data changes rapidly at scale while requiring high performance, durability, and availability.

Which is the most cost-effective service?

## Options

A. Amazon FSx for Windows File Server

B. Amazon EFS

C. Amazon S3

D. Amazon EBS

## Correct Answer

**B. Amazon EFS**

## Explanation

Amazon EFS:
- **NFSv4 protocol**: Native Linux support
- **Concurrent access**: Thousands of instances simultaneously
- **Elastic capacity**: Grows/shrinks automatically
- **Multi-AZ**: Highly available and durable
- **Strong consistency**: File locking support

### Why other options are incorrect:

- **A** - FSx Windows is SMB-based, not NFSv4.

- **C** - S3 is object storage without file locking, not ideal for rapidly changing data.

- **D** - EBS can only attach to one instance (or limited multi-attach).

## References

- https://docs.aws.amazon.com/efs/latest/ug/how-it-works.html
- https://tutorialsdojo.com/amazon-efs/

## Domain

Design High-Performing Architectures
