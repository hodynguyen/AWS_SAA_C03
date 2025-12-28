# Question 53

## Topic
Design Resilient Architectures

## Question
A financial firm is designing an application architecture for its online trading platform that must have high availability and fault tolerance. Their Solutions Architect configured the application to use an Amazon S3 bucket located in the us-east-1 region to store large amounts of intraday financial data. The stored financial data in the bucket must not be affected even if there is an outage in one of the Availability Zones or if there's a regional service failure.

What should the Architect do to avoid any costly service disruptions and ensure data durability?

## Options
A. Create a new S3 bucket in another region and configure Cross-Account Access to the bucket located in us-east-1.

B. Copy the S3 bucket to an EBS-backed EC2 instance.

C. Create a Lifecycle Policy to regularly backup the S3 bucket to Amazon Glacier.

D. Enable Cross-Region Replication.

## Correct Answer
D

## Explanation
In this scenario, you need to enable Cross-Region Replication to ensure that your S3 bucket would not be affected even if there is an outage in one of the Availability Zones or a regional service failure in us-east-1. When you upload your data in S3, your objects are redundantly stored on multiple devices across multiple facilities within the region only, where you created the bucket. Thus, if there is an outage on the entire region, your S3 bucket will be unavailable if you do not enable Cross-Region Replication, which should make your data available to another region.

Note that an Availability Zone (AZ) is more related with Amazon EC2 instances rather than Amazon S3 so if there is any outage in the AZ, the S3 bucket is usually not affected but only the EC2 instances deployed on that zone.

Hence, the correct answer is: Enable Cross-Region Replication.

References:

https://aws.amazon.com/s3/faqs/

https://aws.amazon.com/s3/features/replication/

Check out this Amazon S3 Cheat Sheet:

https://tutorialsdojo.com/amazon-s3/

**Why other options are incorrect:**

- The option that says: Copy the S3 bucket to an EBS-backed EC2 instance is incorrect because EBS is not as durable as Amazon S3. Moreover, if the Availability Zone where the volume is hosted goes down then the data will also be inaccessible.

- The option that says: Create a Lifecycle Policy to regularly backup the S3 bucket to Amazon Glacier is incorrect because Glacier is primarily used for data archival. You also need to replicate your data to another region for better durability.

- The option that says: Create a new S3 bucket in another region and configure Cross-Account Access to the bucket located in us-east-1 is incorrect because Cross-Account Access in Amazon S3 is primarily used if you want to grant access to your objects to another AWS account, and not just to another AWS Region. For example, Account MANILA can grant another AWS account (Account CEBU) permission to access its resources such as buckets and objects. S3 Cross-Account Access does not replicate data from one region to another. A better solution is to enable Cross-Region Replication (CRR) instead.

