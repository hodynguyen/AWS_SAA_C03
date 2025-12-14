# Question 37

A media company wants to ensure that the images it delivers through Amazon CloudFront are compatible across various user devices. The company plans to serve images in WebP format to user agents that support it and return to JPEG format for those that don't.

Which approach would you recommend to meet these requirements while minimizing operational overhead?

## Options

A. Create multiple CloudFront distributions, each serving a specific image format.

B. Implement an image conversion service on Amazon EC2 instances and integrate it with CloudFront.

C. Configure CloudFront behaviors to handle different image formats based on the User-Agent header. Use Lambda@Edge functions to modify the response headers.

D. Generate a CloudFront response headers policy to deliver the suitable image format.

## Correct Answer

**C. Configure CloudFront behaviors to handle different image formats based on the User-Agent header. Use Lambda@Edge functions to modify the response headers and serve the appropriate format.**

## Explanation

Lambda@Edge allows you to run Lambda functions at CloudFront edge locations. You can intercept requests and execute custom code, like dynamically serving different image formats based on User-Agent.

### Why other options are incorrect:

- **A** - Multiple distributions is unnecessary complexity.

- **D** - Response headers policies can't select image formats.

- **B** - EC2 image conversion adds management overhead.

## References

- https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/lambda-at-the-edge.html
- https://tutorialsdojo.com/aws-lambda/

## Domain

Design High-Performing Architectures
