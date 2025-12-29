# Question 49

A developer needs to understand EBS volume types for an EC2 application requiring durable, block-level storage.

Which statements about EBS volume types are true? (Select TWO.)

## Options

A. Provisioned IOPS volumes offer consistent, low-latency performance for I/O intensive applications.

B. Spot volumes provide the lowest cost per gigabyte.

C. SR-IOV volumes are suitable for small to medium databases.

D. General Purpose SSD (gp3) with multi-attach offers multi-AZ resiliency.

E. Magnetic volumes provide the lowest cost per gigabyte.

## Correct Answer

**A. Provisioned IOPS volumes offer consistent, low-latency performance for I/O intensive applications.**

**E. Magnetic volumes provide the lowest cost per gigabyte.**

## Explanation

EBS volume types:
- **Provisioned IOPS (io1/io2)**: Consistent low-latency for databases
- **General Purpose SSD (gp2/gp3)**: Default choice, balanced price/performance
- **Throughput Optimized HDD (st1)**: Sequential workloads, big data
- **Cold HDD (sc1)**: Infrequently accessed data
- **Magnetic**: Previous generation, lowest cost (legacy)

### Why other options are incorrect:

- **B** - "Spot volumes" don't exist. Spot is an EC2 pricing model.

- **C** - SR-IOV is enhanced networking, not an EBS volume type.

- **D** - Multi-attach is single-AZ only, available on io1/io2, not gp3.

## References

- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSVolumeTypes.html
- https://tutorialsdojo.com/amazon-ebs/

## Domain

Design High-Performing Architectures
