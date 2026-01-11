# Question 36

## Topic
Design High-Performing Architectures

## Question
A company has a global online trading platform in which users from all over the world regularly upload terabytes of transactional data to a centralized Amazon S3 bucket.

Which of the following should be used in the present system to improve throughput and ensure consistently fast data transfer to the S3 bucket, regardless of the user's location?

## Options
A. Use Amazon CloudFront Origin Access Control (OAC)

B. S3 Transfer Acceleration

C. FTP

D. AWS Direct Connect

## Correct Answer
B

## Explanation
Amazon S3 Transfer Acceleration enables fast, easy, and secure transfers of files over long distances between your client and your Amazon S3 bucket. Transfer Acceleration leverages Amazon CloudFront's globally distributed AWS Edge Locations. As data arrives at an AWS Edge Location, data is routed to your Amazon S3 bucket over an optimized network path.

**Why other options are incorrect:**
- **Option A** is incorrect because OAC ensures only CloudFront can serve S3 content, it doesn't increase throughput.
- **Option C** is incorrect because FTP does not guarantee fast throughput.
- **Option D** is incorrect because Direct Connect is for on-premises data centers, not users around the world.

## References
- http://docs.aws.amazon.com/AmazonS3/latest/dev/transfer-acceleration.html
- https://docs.aws.amazon.com/AmazonS3/latest/userguide/transfer-acceleration.html
- https://tutorialsdojo.com/amazon-s3/
