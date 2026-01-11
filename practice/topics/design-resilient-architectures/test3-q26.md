# Question 26

## Topic
Design Resilient Architectures

## Question
A company plans to use a durable storage service to store on-premises database backups to the AWS cloud. To move their backup data, they need to use a service that can store and retrieve objects through standard file storage protocols for quick recovery.

Which of the following options will meet this requirement?

## Options
A. Use the AWS Storage Gateway volume gateway to store the backup data and directly access it using Amazon S3 API actions.

B. Use AWS Snowball Edge to directly backup the data in Amazon S3 Glacier.

C. Use the AWS Storage Gateway file gateway to store all the backup data in Amazon S3.

D. Use Amazon EBS volumes to store all the backup data and attach it to an Amazon EC2 instance.

## Correct Answer
C

## Explanation
File Gateway presents a file-based interface to Amazon S3, which appears as a network file share. It enables you to store and retrieve Amazon S3 objects through standard file storage protocols (SMB or NFS). File Gateway allows your existing file-based applications or devices to use secure and durable cloud storage without needing to be modified.

**Why other options are incorrect:**
- **Option A** is incorrect because you cannot directly access volume gateway using Amazon S3 APIs.
- **Option B** is incorrect because Snowball Edge cannot directly integrate backups to S3 Glacier.
- **Option D** is incorrect because EBS is not highly durable like S3 and doesn't support file storage protocols directly.

## References
- https://aws.amazon.com/storagegateway/faqs/
- https://aws.amazon.com/s3/storage-classes/
- https://tutorialsdojo.com/aws-storage-gateway/
