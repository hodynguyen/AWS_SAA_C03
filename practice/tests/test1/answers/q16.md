# Question 16

A financial services company plans to migrate its trading application from on-premises Microsoft Windows Server to Amazon Web Services (AWS). The solution must ensure high availability across multiple Availability Zones and offer low-latency access to block storage.

Which of the following solutions will fulfill these requirements?

## Options

A. Configure the trading application on Amazon EC2 Windows instances across two Availability Zones. Use Amazon Simple Storage Service (Amazon S3) for storage and configure cross-region replication to sync data between S3 buckets in each Availability Zone.

B. Deploy the trading application on Amazon EC2 Windows Server instances across two Availability Zones. Use Amazon FSx for Windows File Server for shared storage.

C. Configure the trading application on Amazon EC2 Windows Server instances across two Availability Zones. Use Amazon FSx for NetApp ONTAP to create a Multi-AZ file system and access the data via iSCSI protocol.

D. Deploy the trading application on Amazon EC2 Windows Server instances across two Availability Zones. Use Amazon Elastic File System (Amazon EFS) to provide shared storage between the instances. Configure Amazon EFS with cross-region replication to sync data across Availability Zones.

## Correct Answer

**C. Configure the trading application on Amazon EC2 Windows Server instances across two Availability Zones. Use Amazon FSx for NetApp ONTAP to create a Multi-AZ file system and access the data via iSCSI protocol.**

## Explanation

Amazon FSx for NetApp ONTAP is a fully managed AWS service that provides high-performance, scalable file storage based on NetApp's ONTAP file system. It offers versatile storage options, supporting both file (NFS, SMB) and block (iSCSI) protocols, making it compatible with Windows, Linux, and macOS environments.

The Amazon FSx for NetApp ONTAP features Multi-AZ file systems designed to ensure continuous availability across AWS Availability Zones. It offers consistent sub-millisecond file operation latencies with SSD storage, essential for block storage workloads in Windows environments. FSx for NetApp ONTAP fully supports block storage protocols like iSCSI, commonly used in Windows Server settings.

### Why other options are incorrect:

- **B** - Amazon FSx for Windows File Server only provides shared, low-latency file storage for Windows environments. It doesn't support low-latency access to shared block storage.

- **D** - Amazon EFS is not optimized for Windows workloads and doesn't offer low-latency block storage.

- **A** - Amazon S3 is primarily an object storage, not block storage. It doesn't offer the low-latency access required for a trading application.

## References

- https://docs.aws.amazon.com/fsx/latest/ONTAPGuide/what-is-fsx-ontap.html
- https://docs.aws.amazon.com/fsx/latest/ONTAPGuide/high-availability-AZ.html
- https://tutorialsdojo.com/amazon-fsx/

## Domain

Design Cost-Optimized Architectures
