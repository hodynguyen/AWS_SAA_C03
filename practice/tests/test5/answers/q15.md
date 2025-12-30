# Question 15

Windows-based applications require scalable file storage for HPC with SMB protocol, NTFS, Active Directory integration, and DFS support.

Which storage service is most suitable?

## Options

A. Amazon FSx for Lustre

B. Amazon FSx for Windows File Server

C. Amazon S3 Glacier Deep Archive

D. AWS DataSync

## Correct Answer

**B. Amazon FSx for Windows File Server**

## Explanation

FSx for Windows File Server:
- **Fully managed Windows file system**: Native NTFS
- **SMB protocol**: Windows-compatible access
- **AD integration**: Join to existing Active Directory
- **DFS support**: Distributed File System namespaces

### Why other options are incorrect:

- **A** - FSx for Lustre is Linux-based, for HPC/ML workloads.

- **C** - Glacier is archival storage, not file system.

- **D** - DataSync is for data transfer, not storage.

## References

- https://aws.amazon.com/fsx/windows/
- https://tutorialsdojo.com/amazon-fsx/

## Domain

Design High-Performing Architectures
