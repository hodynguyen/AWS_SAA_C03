# Question 52

## Topic
Design Secure Architectures

## Question
An online survey startup is collecting real estate data in the United States for several years. The startup already has a total of 5 TB of data stored in an Amazon S3 bucket located in the us-east-1 Region. All real estate data must be shared with a European AWS Managed Service Provider (MSP) Partner which also uses Amazon S3 for storage. Due to budget constraints, the startup must keep its data transfer costs in S3 as low as possible and disable anonymous access.

Which solution meets this requirement MOST cost-effectively?

## Options
A. Enable cross-account access of the startup’s S3 bucket to allow the data downloads and exclusive access from the partner’s AWS account

B. Enable the Requester Pays feature on the Amazon S3 bucket to lower data transfer costs and disable anonymous access

C. Enable S3 Object Lock in governance mode to lower data transfer costs and set a Legal Hold for each object to disable anonymous access

D. Enable Cross-Region Replication(CRR) on the startup’s S3 bucket to automatically copy the S3 content to the partner’s S3 bucket in Europe.

## Correct Answer
B

## Explanation
In general, bucket owners pay for all Amazon S3 storage and data transfer costs that are associated with their bucket. However, you can configure a bucket to be a Requester Pays bucket. With Requester Pays buckets, the requester instead of the bucket owner pays the cost of the request and the data download from the bucket. The bucket owner always pays the cost of storing data.

Typically, you configure buckets to be Requester Pays buckets when you want to share data but not incur charges associated with others accessing the data. For example, you might use Requester Pays buckets when making available large datasets, such as zip code directories, reference data, geospatial information, or web crawling data.

Take note that if you enable Requester Pays on a bucket, anonymous access to that bucket will not be allowed anymore.

You must authenticate all requests involving Requester Pays buckets. The request authentication enables Amazon S3 to identify and charge the requester for their use of the Requester Pays bucket. When the requester assumes an AWS Identity and Access Management (IAM) role before making their request, the account to which the role belongs is charged for the request.

After you configure a bucket to be a Requester Pays bucket, requesters must include x-amz-request-payer in their API request header, for DELETE, GET, HEAD, POST, and PUT requests, or as a parameter in a REST request to show that they understand that they will be charged for the request and the data download.

Hence, the correct answer is: Enable the Requester Pays feature on the Amazon S3 bucket to lower data transfer costs and disable anonymous access

References:

https://docs.aws.amazon.com/AmazonS3/latest/userguide/RequesterPaysBuckets.html

https://docs.aws.amazon.com/AmazonS3/latest/userguide/RequesterPaysExamples.html

Check out this Amazon S3 Cheat Sheet:

https://tutorialsdojo.com/amazon-s3/

**Why other options are incorrect:**

- The option that says: Enable Cross-Region Replication(CRR) on the startup’s S3 bucket to automatically copy the S3 content to the partner’s S3 bucket in Europe is incorrect because CRR incurs data request and transfer fee for inter-region Data Transfer Out (DTO) from your S3 bucket to your destination region. This will effectively increase your data transfer costs instead of lowering it.

- The option that says: Enable cross-account access of the startup’s S3 bucket to allow the data downloads and exclusive access from the partner’s AWS account is incorrect because if the European partner downloads the data from the S3 bucket, then the startup will still be billed for the data transfer costs and not the AWS account of the partner.

- The option that says: Enable S3 Object Lock in governance mode to lower data transfer costs and set a Legal Hold for each object to disable anonymous access is incorrect because the S3 Object Lock feature only prevents objects from being deleted or overwritten for a fixed amount of time. This option will not decrease the data transfer costs at all. Furthermore, the "Legal Hold" option is just a write-once-read-many (WORM) lock retention period for an S3 object that will be applied indefinitely until you explicitly remove it.

