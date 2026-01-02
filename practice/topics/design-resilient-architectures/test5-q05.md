# Question 5

A company needs cloud-backed iSCSI storage volumes. Their analytics app frequently accesses recent data locally while older data is rarely accessed. They want to minimize on-premises storage while maintaining low-latency access.

Which AWS Storage Gateway type should be used?

## Options

A. File Gateway

B. Tape Gateway

C. Volume Gateway in stored mode

D. Volume Gateway in cached mode

## Correct Answer

**D. Volume Gateway in cached mode**

## Explanation

Volume Gateway Cached mode:
- **Primary storage in S3**: Full data stored in AWS
- **Local cache**: Frequently accessed data cached on-premises
- **iSCSI protocol**: Mount as block storage volumes
- **Low latency**: Hot data available locally

### Why other options are incorrect:

- **A** - File Gateway uses NFS/SMB, not iSCSI.

- **B** - Tape Gateway is for backup/archival, not active storage.

- **C** - Stored mode keeps all data on-premises (doesn't minimize local storage).

## References

- https://docs.aws.amazon.com/storagegateway/latest/userguide/StorageGatewayConcepts.html
- https://tutorialsdojo.com/aws-storage-gateway/

## Domain

Design Resilient Architectures
