# Question 11

An organization stores and manages financial records of various companies in its on-premises data center, which is almost out of space. The management decided to move all of their existing records to a cloud storage service. All future financial records will also be stored in the cloud. For additional security, all records must be prevented from being deleted or overwritten.

Which of the following should you do to meet the above requirement?

## Options

A. Use AWS DataSync to move the data. Store all of your data in Amazon S3 and enable object lock.

B. Use AWS Storage Gateway to establish hybrid cloud storage. Store all of your data in Amazon S3 and enable object lock.

C. Use AWS Storage Gateway to establish hybrid cloud storage. Store all of your data in Amazon EBS and enable object lock.

D. Use AWS DataSync to move the data. Store all of your data in Amazon EFS and enable object lock.

## Correct Answer

**A. Use AWS DataSync to move the data. Store all of your data in Amazon S3 and enable object lock.**

## Explanation

AWS DataSync allows you to copy large datasets with millions of files. You can use DataSync to migrate active data to AWS.

S3 Object Lock prevents objects from being deleted or overwritten for a fixed amount of time or indefinitely.

### Why other options are incorrect:

- **B** - Storage Gateway is for hybrid; DataSync is for migration.

- **C** - EBS doesn't support object lock.

- **D** - EFS only supports file locking, not object lock.

## References

- https://aws.amazon.com/datasync/faqs/
- https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock.html
- https://tutorialsdojo.com/aws-datasync/

## Domain

Design Secure Architectures
