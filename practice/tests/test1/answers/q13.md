# Question 13

A government agency plans to store confidential tax documents on AWS. Due to the sensitive information in the files, the Solutions Architect must restrict the data access requests made to the storage solution to a specific Amazon VPC only. The solution should also prevent the files from being deleted or overwritten to meet the regulatory requirement of having a write-once-read-many (WORM) storage model.

Which combination of the following options should the Architect implement? (Select TWO.)

## Options

A. Enable Object Lock but disable Object Versioning on the new Amazon S3 bucket to comply with the write-once-read-many (WORM) storage model requirement.

B. Create a new Amazon S3 bucket with the S3 Object Lock feature enabled. Store the documents in the bucket and set the Legal Hold option for object retention.

C. Store the tax documents in the Amazon S3 Glacier Instant Retrieval storage class. Use the PutBucketPolicy API to apply a bucket policy that restricts access requests to a specific VPC.

D. Configure an Amazon S3 Access Point for the S3 bucket to restrict data access to a particular VPC only.

E. Set up a new Amazon S3 bucket to store the tax documents and integrate it with AWS Network Firewall. Configure the Network Firewall to only accept data access requests from a specific VPC.

## Correct Answers

**B. Create a new Amazon S3 bucket with the S3 Object Lock feature enabled. Store the documents in the bucket and set the Legal Hold option for object retention.**

**D. Configure an Amazon S3 Access Point for the S3 bucket to restrict data access to a particular VPC only.**

## Explanation

Amazon S3 access points simplify data access for any AWS service or customer application that stores data in S3. Access points are named network endpoints that are attached to buckets. You can configure any access point to accept requests only from a virtual private cloud (VPC) to restrict Amazon S3 data access to a private network.

With S3 Object Lock, you can store objects using a write-once-read-many (WORM) model. Object Lock can help prevent objects from being deleted or overwritten for a fixed amount of time or indefinitely. Once S3 Object Lock is enabled on a bucket, it cannot be disabled. Versioning, which is required for Object Lock, cannot be suspended or disabled once Object Lock is enabled.

### Why other options are incorrect:

- **E** - You cannot directly use an AWS Network Firewall to restrict S3 bucket data access requests to a specific Amazon VPC only. You have to use an Amazon S3 Access Point instead.

- **C** - Amazon S3 Glacier Instant Retrieval is just an archive storage class. Using a bucket policy to restrict access from a VPC is less efficient compared to using an S3 Access Point.

- **A** - The Object Versioning feature must also be enabled in order for Object Lock to work.

## References

- https://docs.aws.amazon.com/AmazonS3/latest/userguide/access-points.html
- https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Secure Architectures
