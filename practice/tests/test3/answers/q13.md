# Question 13

## Topic
Design Secure Architectures

## Question
A company has clients all across the globe that access product files stored in several Amazon S3 buckets, which are behind each of the respective Amazon CloudFront web distributions. The company currently wants to deliver content to a specific client, ensuring that only that client can access the data. At present, all clients can access the S3 buckets directly using an S3 URL or through the CloudFront distribution. The Solutions Architect must serve the private content via CloudFront only, to secure the distribution of files.

Which combination of actions should the Architect implement to meet the above requirements? (Select TWO.)

## Options
A. Enable the Origin Shield feature of the CloudFront distribution to protect the files from unauthorized access.

B. Restrict access to files in the origin by creating an origin access control (OAC) and giving it permission to read the files in the bucket.

C. Generate an S3 presigned URL to ensure that only the client can access the files.

D. Create a custom CloudFront function to check and ensure that only their clients can access the files.

E. Require the users to access the private content by using special CloudFront signed URLs or signed cookies.

## Correct Answers
**B. Restrict access to files in the origin by creating an origin access control (OAC) and giving it permission to read the files in the bucket.**

**E. Require the users to access the private content by using special CloudFront signed URLs or signed cookies.**

## Explanation
To securely serve private content by using CloudFront, you can do the following:

- Require that your users access your private content by using special CloudFront signed URLs or signed cookies.
- Require that your users access your Amazon S3 content by using CloudFront URLs, not Amazon S3 URLs, by setting up an origin access control (OAC).

**Why other options are incorrect:**
- **Option A** is incorrect because Origin Shield is for improving load times and availability, not for security.
- **Option C** is incorrect because S3 presigned URLs don't scale well for multiple files or users.
- **Option D** is incorrect because CloudFront Functions are for customizations, not for enforcing security.

## References
- https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/PrivateContent.html
- https://docs.aws.amazon.com/AmazonS3/latest/dev/PresignedUrlUploadObject.html
- https://tutorialsdojo.com/amazon-cloudfront/
