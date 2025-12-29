# Question 8

An EBS snapshot is being created at midnight. A production incident requires changes to both the EC2 instance and EBS volume while the snapshot is in progress.

Which statement is true about EBS volume usage during snapshot?

## Options

A. EBS volume cannot be detached/attached until snapshot completes.

B. EBS volume cannot be used until snapshot completes.

C. EBS volume can only be used in read-only mode.

D. EBS volume can be used while snapshot is in progress.

## Correct Answer

**D. EBS volume can be used while snapshot is in progress.**

## Explanation

EBS snapshots are asynchronous:
- **Point-in-time capture**: Snapshot created immediately
- **Background transfer**: Data copied to S3 in background
- **No interruption**: Volume fully usable during snapshot
- **Consistent reads/writes**: Volume operations continue normally

### Why other options are incorrect:

- **A** - Volume can be detached during snapshot (snapshot continues from S3).

- **B, C** - Volume has full read/write access during snapshot.

## References

- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-creating-snapshot.html
- https://tutorialsdojo.com/amazon-ebs/

## Domain

Design Secure Architectures
