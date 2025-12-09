# Question 53

A logistics company plans to automate its order management application. The company wants to use SFTP file transfer for uploading business-critical documents. Since the files are confidential, encryption at rest is required, and high availability must be ensured. Additionally, each file must be automatically deleted one month after creation.

Which of the following options should be implemented to meet the company's requirements with the least operational overhead?

## Options

A. Create an Amazon S3 bucket with encryption enabled. Configure AWS Transfer for SFTP to securely upload files to the S3 bucket. Configure the retention policy on the SFTP server to delete files after a month.

B. Create an Amazon Elastic File System (Amazon EFS) and enable encryption. Configure AWS Transfer for SFTP to securely upload files to the EFS file system. Apply an EFS lifecycle policy to delete files after 30 days.

C. Create an Amazon S3 bucket with encryption enabled. Launch an AWS Transfer for SFTP endpoint to securely upload files to the S3 bucket. Configure an S3 lifecycle rule to delete files after a month.

D. Provision an Amazon EC2 instance and install the SFTP service. Mount an encrypted Amazon EFS file system on the EC2 instance.

## Correct Answer

**C. Create an Amazon S3 bucket with encryption enabled. Launch an AWS Transfer for SFTP endpoint to securely upload files to the S3 bucket. Configure an S3 lifecycle rule to delete files after a month.**

## Explanation

AWS Transfer for SFTP enables you to move your file transfer workloads to AWS without modifying applications. You can use S3 as the storage service for your SFTP-enabled server.

S3 Lifecycle rules can define expiration actions to delete objects after a specified period.

### Why other options are incorrect:

- **A** - There's no retention policy option on AWS Transfer for SFTP. It must be configured on S3.

- **B** - EFS lifecycle management only transitions files between storage tiers, it doesn't delete files.

- **D** - This requires managing EC2 instances and SFTP service, adding operational overhead.

## References

- https://aws.amazon.com/aws-transfer-family/
- https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lifecycle-mgmt.html
- https://tutorialsdojo.com/aws-transfer-family/

## Domain

Design Resilient Architectures
