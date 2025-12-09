# Question 8

A Solutions Architect is hosting a website in an Amazon S3 bucket named tutorialsdojo. The users load the website using the following URL: http://tutorialsdojo.s3-website-us-east-1.amazonaws.com. A new requirement has been introduced to add JavaScript on the webpages to make authenticated HTTP GET requests against the same bucket using the S3 API endpoint (tutorialsdojo.s3.amazonaws.com). However, upon testing, the web browser blocks JavaScript from allowing those requests.

Which of the following options is the MOST suitable solution to implement for this scenario?

## Options

A. Enable Cross-Region Replication (CRR).

B. Enable Cross-origin resource sharing (CORS) configuration in the bucket.

C. Enable Cross-Zone Load Balancing.

D. Enable cross-account access.

## Correct Answer

**B. Enable Cross-origin resource sharing (CORS) configuration in the bucket.**

## Explanation

Cross-origin resource sharing (CORS) defines a way for client web applications that are loaded in one domain to interact with resources in a different domain. With CORS support, you can build rich client-side web applications with Amazon S3 and selectively allow cross-origin access to your Amazon S3 resources.

In this scenario, you are hosting a website in an Amazon S3 bucket and want to use JavaScript on the webpages to make authenticated GET and PUT requests against the same bucket by using the Amazon S3 API endpoint. A browser would normally block JavaScript from allowing those requests, but with CORS you can configure your bucket to explicitly enable cross-origin requests.

### Why other options are incorrect:

- **D** - Cross-account access is just a feature in IAM and not in Amazon S3.

- **C** - Cross-Zone Load Balancing is only used in ELB and not in S3.

- **A** - CRR is a bucket-level configuration that enables automatic, asynchronous copying of objects across buckets in different AWS Regions.

## References

- http://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html
- https://docs.aws.amazon.com/AmazonS3/latest/dev/ManageCorsUsing.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Secure Architectures
