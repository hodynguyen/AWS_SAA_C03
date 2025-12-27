# Question 51

## Topic
Design Secure Architectures

## Question
A Solutions Architect is working for a large global media company with multiple office locations all around the world. The Architect is instructed to build a system to distribute training videos to all employees.

Using Amazon CloudFront, what method would be used to serve content that is stored in Amazon S3 but not publicly accessible from S3 directly?

## Options
A. Create an Identity and Access Management (IAM) user for CloudFront and grant access to the objects in your S3 bucket to that IAM user.

B. Create an S3 bucket policy that lists the CloudFront distribution ID as the principal and the target bucket as the Amazon Resource Name (ARN).

C. Create an Origin Access Control (OAC) for CloudFront and grant access to the objects in your S3 bucket to that OAC.

D. Create a web ACL in AWS WAF to block any public S3 access and attach it to the CloudFront distribution.

## Correct Answer
C

## Explanation
When you create or update a distribution in CloudFront, you can add an origin access Control (OAC) and automatically update the bucket policy to give the origin access control permission to access your bucket. Alternatively, you can choose to manually change the bucket policy or change ACLs, which control permissions on individual objects in your bucket.

You can update the Amazon S3 bucket policy using either the AWS Management Console or the Amazon S3 API:

- Grant the CloudFront origin access control the applicable permissions on the bucket.

- Deny access to anyone that you don't want to have access using Amazon S3 URLs.

Hence, the correct answer is: Create an Origin Access Control (OAC) for CloudFront and grant access to the objects in your S3 bucket to that OAC.

References:

https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html

https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/SecurityAndPrivateContent.html

Check out this Amazon CloudFront Cheat Sheet:

https://tutorialsdojo.com/amazon-cloudfront/

Comparison of AWS Services Cheat Sheets:

https://tutorialsdojo.com/comparison-of-aws-services/

**Why other options are incorrect:**

- The option that says: Create an Identity and Access Management (IAM) user for CloudFront and grant access to the objects in your S3 bucket to that IAM user is incorrect because you cannot directly create an IAM User for a specific Amazon CloudFront distribution. You have to use an origin access control (OAC) instead.

- The option that says: Create an S3 bucket policy that lists the CloudFront distribution ID as the principal and the target bucket as the Amazon Resource Name (ARN) is incorrect. While you can typically specify AWS accounts, IAM users, and IAM roles as principals in an S3 bucket policy, you cannot directly use a CloudFront distribution ID as a principal in an S3 bucket policy. Instead, you must define the CloudFront service as the Principal and restrict access to your CF distribution using the Condition policy. Therefore, this is not the correct method for the given scenario.

- The option that says: Create a web ACL in AWS WAF to block any public S3 access and attach it to the CloudFront distribution is incorrect because AWS WAF is primarily used to protect your applications from common web vulnerabilities and not to ensure exclusive access to CloudFront.

