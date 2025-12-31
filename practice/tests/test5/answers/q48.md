# Question 48

Dedicated physical server (no virtualization) needs NFS storage with cloud backup to S3.

Which is the most suitable solution?

## Options

A. Storage Gateway VM appliance with File Gateway.

B. Storage Gateway hardware appliance with File Gateway and S3 backup.

C. Storage Gateway hardware appliance with Volume Gateway and S3 backup.

D. Storage Gateway hardware appliance with Volume Gateway.

## Correct Answer

**B. Storage Gateway hardware appliance with File Gateway and S3 backup.**

## Explanation

Solution requirements:
- **No virtualization**: Hardware appliance (not VM)
- **NFS protocol**: File Gateway (not Volume Gateway which uses iSCSI)
- **S3 backup**: File Gateway stores in S3

### Why other options are incorrect:

- **A** - VM appliance requires virtualization.

- **C, D** - Volume Gateway uses iSCSI, not NFS.

## References

- https://docs.aws.amazon.com/storagegateway/latest/userguide/hardware-appliance.html
- https://tutorialsdojo.com/aws-storage-gateway/

## Domain

Design High-Performing Architectures
