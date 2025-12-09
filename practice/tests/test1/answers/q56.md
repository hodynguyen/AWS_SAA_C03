# Question 56

A popular social media website uses a Amazon CloudFront web distribution to serve static content to millions of users around the globe. Recently, the website has received a number of complaints about long login times. Additionally, there are instances where users encounter HTTP 504 errors.

Which of the following options should be used together to set up a cost-effective solution that improves the application's performance? (Select TWO.)

## Options

A. Implement an origin failover by creating an origin group that includes two origins. Assign one as the primary origin and the other as secondary.

B. Deploy your application to multiple AWS regions to accommodate your users around the world.

C. Establish multiple Amazon VPCs in different AWS regions and configure a transit VPC.

D. Customize the content that the CloudFront web distribution delivers to your users using Lambda@Edge, which allows your AWS Lambda functions to execute the authentication process in AWS locations closer to the users.

E. Configure your origin to add a Cache-Control max-age directive to your objects.

## Correct Answers

**A. Implement an origin failover by creating an origin group that includes two origins. Assign one as the primary origin and the other as secondary, which enables CloudFront to automatically switch to if the primary origin encounters specific HTTP status code failure responses.**

**D. Customize the content that the CloudFront web distribution delivers to your users using Lambda@Edge, which allows your AWS Lambda functions to execute the authentication process in AWS locations closer to the users.**

## Explanation

Lambda@Edge lets you run Lambda functions to customize the content that CloudFront delivers, executing the functions in AWS locations closer to the viewer.

Origin failover allows CloudFront to automatically switch to a secondary origin when the primary origin fails, addressing HTTP 504 errors.

### Why other options are incorrect:

- **C** - Setting up VPCs and transit VPCs adds complexity and cost.

- **E** - Improving cache hit ratio doesn't address the authentication/login performance issue.

- **B** - Deploying to multiple regions is costly; Lambda@Edge is more cost-effective.

## References

- https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/high_availability_origin_failover.html
- https://docs.aws.amazon.com/lambda/latest/dg/lambda-edge.html
- https://tutorialsdojo.com/amazon-cloudfront/

## Domain

Design High-Performing Architectures
