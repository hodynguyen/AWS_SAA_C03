# Question 62

A company has a hybrid cloud architecture that connects its on-premises data center and cloud infrastructure in AWS. It requires a durable storage backup for its corporate documents stored on-premises and a local cache that provides low-latency access to recently accessed data to reduce data egress charges. The documents must be stored on and retrieved from AWS via the Server Message Block (SMB) protocol. These files must be immediately accessible within minutes for six months and archived for another decade to meet data compliance.

Which of the following is the best and most cost-effective approach to implement in this scenario?

## Options

A. Launch a new file gateway that connects to your on-premises data center using AWS Storage Gateway. Upload the documents to the file gateway and set up a lifecycle policy to move the data into Glacier for data archival.

B. Use AWS DataSync to transfer all files from the on-premises network directly to an Amazon S3 bucket.

C. Launch a new tape gateway that connects to your on-premises data center using AWS Storage Gateway.

D. Establish a Direct Connect connection to integrate your on-premises network to your VPC. Upload the documents on Amazon EBS Volumes.

## Correct Answer

**A. Launch a new file gateway that connects to your on-premises data center using AWS Storage Gateway. Upload the documents to the file gateway and set up a lifecycle policy to move the data into Glacier for data archival.**

## Explanation

A file gateway supports file interfaces into Amazon S3 using NFS and SMB protocols. The file gateway provides local caching for low-latency access to recently accessed data.

You can use S3 lifecycle policies to transition objects to Glacier for long-term archival.

### Why other options are incorrect:

- **C** - Tape gateway doesn't provide immediate retrieval within minutes or local caching.

- **D** - EBS is less durable than S3 and more costly for this use case.

- **B** - DataSync doesn't offer local caching, increasing data egress charges.

## References

- https://docs.aws.amazon.com/storagegateway/latest/userguide/StorageGatewayConcepts.html
- https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Resilient Architectures
