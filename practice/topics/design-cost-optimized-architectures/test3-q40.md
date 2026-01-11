# Question 40

## Topic
Design Cost-Optimized Architectures

## Question
A Solutions Architect is working for a financial company. The manager wants to have the ability to automatically transfer obsolete data from their S3 bucket to a low-cost storage system in AWS after a certain period of time.

What is the best solution that the Architect can provide to them?

## Options
A. Use an EC2 instance and a scheduled job to transfer the obsolete data from their S3 location to Amazon S3 Glacier.

B. Use Amazon Timestream.

C. Use Lifecycle Policies in S3 to move obsolete data to Glacier.

D. Use Amazon SQS.

## Correct Answer
C

## Explanation
Lifecycle configuration in Amazon S3 enables you to specify the lifecycle management of objects in a bucket. You can define:

- **Transition actions** – Define when objects transition to another storage class. For example, you may choose to transition objects to STANDARD_IA after 30 days, or archive objects to GLACIER after one year.
- **Expiration actions** – Specify when the objects expire.

**Why other options are incorrect:**
- **Option A** is incorrect because you don't need a scheduled job in EC2; you can use lifecycle policies.
- **Option B** is incorrect because Timestream is for time-series data, not for moving S3 data.
- **Option D** is incorrect because SQS is a message queuing service, not a storage service.

## References
- http://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html
- https://aws.amazon.com/blogs/aws/archive-s3-to-glacier/
- https://tutorialsdojo.com/amazon-s3/
