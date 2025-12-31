# Question 43

EC2 with encrypted EBS volumes.

Which statements are true about encrypted EBS? (Select TWO.)

## Options

A. Snapshots from encrypted volumes are not encrypted.

B. Snapshots are automatically encrypted.

C. Only data at rest is encrypted, not data in transit.

D. All data moving between volume and instance are encrypted.

E. Snapshots are not automatically encrypted.

## Correct Answer

**B. Snapshots are automatically encrypted.**

**D. All data moving between volume and instance are encrypted.**

## Explanation

EBS encryption covers:
- **Data at rest**: Encrypted on the volume
- **Data in transit**: Encrypted between EC2 and EBS
- **Snapshots**: Automatically encrypted
- **Volumes from snapshots**: Also encrypted

Uses AES-256 encryption with AWS-managed or customer-managed keys.

### Why other options are incorrect:

- **A, E** - Snapshots ARE automatically encrypted.

- **C** - Data in transit IS also encrypted.

## References

- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSEncryption.html
- https://tutorialsdojo.com/amazon-ebs/

## Domain

Design Secure Architectures
