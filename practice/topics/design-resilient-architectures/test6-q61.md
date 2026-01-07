# Question 61

On-premises backup via SMB. 48 hours immediate access, older can have delay. LEAST configuration effort.

Which solution?

## Options

A. EFS file system + NFS share.

B. FSx for Windows File Server.

C. AWS Backup plan.

D. Storage Gateway File gateway with SMB.

## Correct Answer

**D. Storage Gateway File gateway with SMB.**

## Explanation

Storage Gateway for on-premises backup:
- **SMB protocol**: Windows-compatible
- **Local cache**: 48 hours immediate access
- **S3 backend**: Older data with slight delay
- **Minimal setup**: Mount as local drive

### Why other options are incorrect:

- **A** - EFS uses NFS, not SMB.

- **B** - Requires Direct Connect/VPN setup.

- **C** - AWS Backup only for AWS resources.

## References

- https://aws.amazon.com/storagegateway/faqs/
- https://tutorialsdojo.com/aws-storage-gateway/

## Domain

Design Resilient Architectures
