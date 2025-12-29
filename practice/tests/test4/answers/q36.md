# Question 36

An autonomous vehicle project requires HPC with low-latency networking, OS-bypass functionality, and high throughput for inter-instance communication on Linux EC2 instances.

What is the most suitable solution?

## Options

A. Attach an Elastic Network Interface (ENI) to each instance.

B. Attach an Elastic Fabric Adapter (EFA) to each instance.

C. Attach an Elastic Network Adapter (ENA) to each instance.

D. Attach a Private Virtual Interface (VIF) to each instance.

## Correct Answer

**B. Attach an Elastic Fabric Adapter (EFA) to each instance.**

## Explanation

EFA provides:
- **OS-bypass**: HPC applications communicate directly with network hardware
- **Low latency**: Bypasses the OS kernel for minimal overhead
- **High throughput**: Optimized for inter-instance MPI/NCCL communication
- **HPC integration**: Supports Libfabric, Open MPI, Intel MPI, NVIDIA NCCL

### Why other options are incorrect:

- **A** - ENI is a basic virtual network interface without OS-bypass capability.

- **C** - ENA provides enhanced networking but no OS-bypass functionality.

- **D** - Private VIF is for Direct Connect to VPC, not HPC networking.

## References

- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/efa.html
- https://tutorialsdojo.com/elastic-fabric-adapter-efa/

## Domain

Design High-Performing Architectures
