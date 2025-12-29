# Question 12

A company uses an On-Demand EC2 instance with an Instance Store-Backed AMI. The application is being decommissioned.

When the instance is terminated, what happens to the data on the root volume?

## Options

A. Data is automatically saved as an EBS snapshot.

B. Data is unavailable until the instance is restarted.

C. Data is automatically saved as an EBS volume.

D. Data is automatically deleted.

## Correct Answer

**D. Data is automatically deleted.**

## Explanation

Instance store volumes are ephemeral storage physically attached to the host. Data on instance store persists only during the instance's lifetime. When the instance is terminated, the data is permanently deleted and cannot be recovered.

### Why other options are incorrect:

- **A** - Instance store data cannot be saved as EBS snapshots. Only EBS volumes support snapshots.

- **B** - Terminated instances cannot be restarted. Instance store data is lost permanently.

- **C** - Instance store data is not converted to EBS volumes on termination.

## References

- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ComponentsAMIs.html
- https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/

## Domain

Design Secure Architectures
