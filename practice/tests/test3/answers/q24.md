# Question 24

## Topic
Design Cost-Optimized Architectures

## Question
A company has an e-commerce application that saves the transaction logs to an S3 bucket. You are instructed by the CTO to configure the application to keep the transaction logs for one month for troubleshooting purposes, and then afterward, purge the logs.

What should you do to accomplish this requirement?

## Options
A. Create a new IAM policy for the Amazon S3 bucket that automatically deletes the logs after a month

B. Add a new bucket policy on the Amazon S3 bucket.

C. Enable CORS on the Amazon S3 bucket which will enable the automatic monthly deletion of data

D. Configure the lifecycle configuration rules on the Amazon S3 bucket to purge the transaction logs after a month

## Correct Answer
D

## Explanation
Lifecycle configuration enables you to specify the lifecycle management of objects in a bucket. The configuration is a set of one or more rules, where each rule defines an action for Amazon S3 to apply:

- **Transition actions** – Define when objects transition to another storage class.
- **Expiration actions** – Specify when the objects expire. Amazon S3 deletes the expired objects on your behalf.

**Why other options are incorrect:**
- **Option A** is incorrect because IAM policies specify allowed or denied actions, not automatic deletion.
- **Option B** is incorrect because bucket policies grant access permissions, not automatic deletion.
- **Option C** is incorrect because CORS is for client web applications to interact with resources in different domains.

## References
- https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html
- https://tutorialsdojo.com/amazon-s3/
