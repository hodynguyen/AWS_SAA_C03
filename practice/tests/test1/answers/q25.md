# Question 25

A travel photo-sharing website is using Amazon S3 to serve high-quality photos to visitors. After a few days, it was discovered that other travel websites are linking to and using these photos. This has resulted in financial losses for the business.

What is the MOST effective method to mitigate this issue?

## Options

A. Store and privately serve the high-quality photos on Amazon WorkDocs instead.

B. Configure your S3 bucket to remove public read access and use pre-signed URLs with expiry dates.

C. Block the IP addresses of the offending websites using NACL.

D. Use Amazon CloudFront distributions for your photos.

## Correct Answer

**B. Configure your S3 bucket to remove public read access and use pre-signed URLs with expiry dates.**

## Explanation

In Amazon S3, all objects are private by default. Only the object owner has permission to access these objects. However, the object owner can optionally share objects with others by creating a pre-signed URL, using their own security credentials, to grant time-limited permission to download the objects.

When you create a pre-signed URL for your object, you must provide your security credentials, specify a bucket name, an object key, specify the HTTP method (GET to download the object), and the expiration date and time. The pre-signed URLs are valid only for the specified duration.

### Why other options are incorrect:

- **D** - CloudFront is primarily a content delivery network service that speeds up the delivery of content to your customers.

- **C** - Blocking IP addresses using NACLs is not very efficient because a quick change in IP address would easily bypass this configuration.

- **A** - WorkDocs is a content creation, storage, and collaboration service. It is not suitable for serving static content like Amazon S3.

## References

- https://docs.aws.amazon.com/AmazonS3/latest/dev/ShareObjectPreSignedURL.html
- https://docs.aws.amazon.com/AmazonS3/latest/dev/ObjectOperations.html
- https://tutorialsdojo.com/amazon-cloudfront/

## Domain

Design Resilient Architectures
