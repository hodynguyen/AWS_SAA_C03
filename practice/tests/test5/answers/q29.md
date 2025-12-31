# Question 29

A Windows-based HPC cluster on t3a.medium EC2 instances needs higher bandwidth, higher PPS, and lower inter-instance latencies.

Which is the most suitable and cost-effective solution?

## Options

A. Enable Enhanced Networking with EFA on Windows instances.

B. Use AWS ParallelCluster.

C. Enable Enhanced Networking with Intel 82599 VF interface.

D. Enable Enhanced Networking with ENA on Windows instances.

## Correct Answer

**D. Enable Enhanced Networking with ENA on Windows instances.**

## Explanation

Elastic Network Adapter (ENA):
- **Enhanced networking**: SR-IOV for high performance
- **Higher bandwidth**: Up to 100 Gbps
- **Lower latency**: Better inter-instance communication
- **Windows supported**: Full support

### Why other options are incorrect:

- **A** - EFA OS-bypass features not supported on Windows. Acts as regular ENA.

- **B** - ParallelCluster is management tool, doesn't improve networking.

- **C** - Intel 82599 VF doesn't support t3a instance type.

## References

- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/enhanced-networking.html
- https://tutorialsdojo.com/amazon-ec2/

## Domain

Design High-Performing Architectures
