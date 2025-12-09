# Question 59

A company plans to migrate its on-premises workload to AWS. The current architecture is composed of a Microsoft SharePoint server that uses a Windows shared file storage. The Solutions Architect needs to use a cloud storage solution that is highly available and can be integrated with Active Directory for access control and authentication.

Which of the following options can satisfy the given requirement?

## Options

A. Create a file system using Amazon EFS and join it to an Active Directory domain.

B. Launch an Amazon EC2 Windows Server to mount a new Amazon S3 bucket as a file volume.

C. Create a file system using Amazon FSx for Windows File Server and join it to an Active Directory domain in AWS.

D. Create a Network File System (NFS) file share using AWS Storage Gateway.

## Correct Answer

**C. Create a file system using Amazon FSx for Windows File Server and join it to an Active Directory domain in AWS.**

## Explanation

Amazon FSx for Windows File Server provides fully managed Microsoft Windows file servers with native Windows file system support. It supports Active Directory integration for user authentication and access control.

It uses the SMB protocol, which is what Windows file shares use.

### Why other options are incorrect:

- **A** - Amazon EFS only supports Linux workloads, not Windows.

- **B** - Amazon S3 can't integrate with Active Directory for authentication/access control.

- **D** - NFS file share is for Linux systems. Windows requires SMB file share.

## References

- https://docs.aws.amazon.com/fsx/latest/WindowsGuide/aws-ad-integration-fsxW.html
- https://aws.amazon.com/fsx/windows/faqs/
- https://tutorialsdojo.com/amazon-fsx/

## Domain

Design Resilient Architectures
