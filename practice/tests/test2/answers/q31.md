# Question 31

A solutions architect is instructed to host a website that consists of HTML, CSS, and some Javascript files. The web pages will display several high-resolution images. The website should have optimal loading times and be able to respond to high request rates.

Which of the following architectures can provide the most cost-effective and fastest loading experience?

## Options

A. Launch an Auto Scaling Group using an AMI that has a pre-configured Apache web server, then configure the scaling policy accordingly. Store the images in an Elastic Block Store.

B. Host the website in an AWS Elastic Beanstalk environment. Upload the images in an S3 bucket. Use CloudFront as a CDN.

C. Upload the HTML, CSS, Javascript, and the images in a single bucket. Then enable website hosting. Create a CloudFront distribution and point the domain on the S3 website endpoint.

D. Host the website using an Nginx server in an EC2 instance. Upload the images in an S3 bucket. Use CloudFront as a CDN.

## Correct Answer

**C. Upload the HTML, CSS, Javascript, and the images in a single bucket. Then enable website hosting. Create a CloudFront distribution and point the domain on the S3 website endpoint.**

## Explanation

Amazon S3 is a cost-effective solution for hosting static websites. S3 automatically scales to high requests, and you only pay for what you use. CloudFront integration improves loading times by caching content at edge locations.

### Why other options are incorrect:

- **D** - EC2 web servers cost more than S3 for static content.

- **A** - ASG with EC2 is overkill for static websites.

- **B** - Elastic Beanstalk is more expensive for static files.

## References

- https://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteHosting.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Cost-Optimized Architectures
