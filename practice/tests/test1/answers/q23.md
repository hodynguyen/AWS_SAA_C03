# Question 23

A company has a web application that uses Internet Information Services (IIS) for Windows Server. A file share is used to store the application data on the network-attached storage of the company's on-premises data center. To achieve a highly available system, the company plans to migrate the application and file share to AWS.

Which of the following can be used to fulfill this requirement?

## Options

A. Migrate the existing file share configuration to Amazon EBS.

B. Migrate the existing file share configuration to Amazon EFS.

C. Migrate the existing file share configuration to AWS Storage Gateway.

D. Migrate the existing file share configuration to Amazon FSx for Windows File Server.

## Correct Answer

**D. Migrate the existing file share configuration to Amazon FSx for Windows File Server.**

## Explanation

Amazon FSx for Windows File Server provides fully managed Microsoft Windows file servers, backed by a fully native Windows file system. Amazon FSx for Windows File Server has the features, performance, and compatibility to easily lift and shift enterprise applications to the AWS Cloud. It is accessible from Windows, Linux, and macOS compute instances and devices.

A file share is a specific folder in your file system, including the folder's subfolders, which you make accessible to your compute instances via the SMB protocol. To migrate file share configurations from your on-premises file system, you must migrate your files first to Amazon FSx before migrating your file share configuration.

### Why other options are incorrect:

- **C** - AWS Storage Gateway is primarily used to integrate your on-premises network to AWS but not for migrating your applications. Using a file share in Storage Gateway implies you will still keep your on-premises systems.

- **B** - Amazon EFS only supports Linux workloads. The scenario states the company is using a file share that runs on a Windows server.

- **A** - EBS is primarily used as block storage for EC2 instances and not as a shared file system. It does not support SMB protocol.

## References

- https://aws.amazon.com/fsx/windows/faqs/
- https://docs.aws.amazon.com/fsx/latest/WindowsGuide/migrate-file-share-config-to-fsx.html
- https://tutorialsdojo.com/amazon-fsx/

## Domain

Design High-Performing Architectures
