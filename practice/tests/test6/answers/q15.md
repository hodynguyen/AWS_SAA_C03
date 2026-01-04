# Question 15

Unencrypted EBS snapshots. All new volumes from them must be automatically encrypted.

What should be done?

## Options

A. Enable EBS Encryption By Default for the Region.

B. Enable EBS Encryption By Default for specific volumes.

C. Launch new volumes with symmetric KMS keys.

D. Launch new volumes with asymmetric KMS keys.

## Correct Answer

**A. Enable EBS Encryption By Default for the Region.**

## Explanation

EBS Encryption By Default:
- **Region-level setting**: All new volumes encrypted
- **Automatic**: No manual steps needed
- **Existing snapshots**: Can create encrypted copies
- **Default key**: Uses aws/ebs or custom CMK

### Why other options are incorrect:

- **B** - Can't enable for specific volumes; it's region-wide.

- **C** - Manual; not "automatically" encrypted.

- **D** - EBS doesn't support asymmetric keys.

## References

- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSEncryption.html
- https://tutorialsdojo.com/amazon-ebs/

## Domain

Design Secure Architectures
