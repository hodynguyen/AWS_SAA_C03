# Question 14

Large EC2 with EBS and Enhanced Networking for training portal.

What are valid use cases for Enhanced Networking? (Select TWO.)

## Options

A. Low packet-per-second performance.

B. Higher packet per second (PPS) performance.

C. High latency networking.

D. Lower inter-instance latencies.

E. Dedicated connection to on-premises.

## Correct Answer

**B. Higher packet per second (PPS) performance.**

**D. Lower inter-instance latencies.**

## Explanation

Enhanced Networking (SR-IOV):
- **Higher PPS**: More packets processed
- **Lower latency**: Faster inter-instance communication
- **Lower CPU**: Hardware-based virtualization
- **No extra cost**: Free feature

### Why other options are incorrect:

- **A, C** - Enhanced networking improves, not lowers performance.

- **E** - Use Direct Connect for on-premises connections.

## References

- http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/enhanced-networking.html
- https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/

## Domain

Design High-Performing Architectures
