# Question 57

## Topic
Design Cost-Optimized Architectures

## Question
A web application is hosted in an Auto Scaling group of EC2 instances deployed across multiple Availability Zones behind an Application Load Balancer. You need to implement an SSL solution for your system to improve its security which is why you requested an SSL/TLS certificate from a third-party certificate authority (CA).

Where can you safely import the SSL/TLS certificate of your application? (Select TWO.)

## Options
A. AWS Certificate Manager

B. IAM certificate store

C. A private S3 bucket with versioning enabled

D. An S3 bucket configured with server-side encryption with customer-provided encryption keys (SSE-C)

E. CloudFront

## Correct Answer
A, B

## Explanation
If you got your certificate from a third-party CA, import the certificate into ACM or upload it to the IAM certificate store. Hence, AWS Certificate Manager and IAM certificate store are the correct answers.

ACM lets you import third-party certificates from the ACM console, as well as programmatically. If ACM is not available in your region, use AWS CLI to upload your third-party certificate to the IAM certificate store.

A private S3 bucket with versioning enabled and an S3 bucket configured with server-side encryption with customer-provided encryption keys (SSE-C) are both incorrect as S3 is not a suitable service to store the SSL certificate.

CloudFront is incorrect. Although you can upload certificates to CloudFront, it doesn't mean that you can import SSL certificates on it. You would not be able to export the certificate that you have loaded in CloudFront nor assign them to your EC2 or ELB instances as it would be tied to a single CloudFront distribution.

Reference:

https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/cnames-and-https-procedures.html#cnames-and-https-uploading-certificates

Check out this Amazon CloudFront Cheat Sheet:

https://tutorialsdojo.com/amazon-cloudfront/

Tutorials Dojo's AWS Certified Solutions Architect Associate Exam Study Guide:

https://tutorialsdojo.com/aws-certified-solutions-architect-associate-saa-c02/


