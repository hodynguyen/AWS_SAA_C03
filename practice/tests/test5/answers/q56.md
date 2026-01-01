# Question 56

.NET Windows EC2 app needs shared file system with high throughput/IOPS and Active Directory integration.

Which is the most suitable service?

## Options

A. Amazon FSx for Windows File Server

B. AWS Storage Gateway - File Gateway

C. Amazon EBS Provisioned IOPS SSD

D. Amazon EFS

## Correct Answer

**A. Amazon FSx for Windows File Server**

## Explanation

FSx for Windows File Server:
- **SMB protocol**: Windows-native file sharing
- **Active Directory**: Full integration
- **High performance**: Up to GB/s throughput
- **NTFS features**: Quotas, ACLs, DFS namespaces
- **Fully managed**: No Windows Server to maintain

### Why other options are incorrect:

- **B** - File Gateway is for hybrid storage to S3.

- **C** - EBS is block storage, single-instance only.

- **D** - EFS uses NFS, not SMB; Linux-focused.

## References

- https://aws.amazon.com/fsx/windows/
- https://tutorialsdojo.com/amazon-fsx/

## Domain

Design High-Performing Architectures
