# Question 37

A company has a web application that uses Amazon CloudFront to distribute its images, videos, and other static content stored in its Amazon S3 bucket to users around the world. The company has recently introduced a new member-only access feature for some of its high-quality media files. There is a requirement to provide access to multiple private media files only to paying subscribers without having to change the current URLs.

Which of the following is the most suitable solution to implement to satisfy this requirement?

## Options

A. Create a Signed URL with a custom policy which only allows the members to see the private files.

B. Configure your CloudFront distribution to use Match Viewer as its Origin Protocol Policy.

C. Use Signed Cookies to control who can access the private files in your CloudFront distribution by modifying your application to determine whether a user should have access to your content.

D. Configure your CloudFront distribution to use Field-Level Encryption to protect your private data and only allow access to members.

## Correct Answer

**C. Use Signed Cookies to control who can access the private files in your CloudFront distribution by modifying your application to determine whether a user should have access to your content. For members, send the required Set-Cookie headers to the viewer which will unlock the content only to them.**

## Explanation

Use signed cookies for the following cases:
- You want to provide access to multiple restricted files
- You don't want to change your current URLs

Use signed URLs when:
- You want to restrict access to individual files
- Your users are using a client that doesn't support cookies

### Why other options are incorrect:

- **B** - Match Viewer is an Origin Protocol Policy for HTTP/HTTPS, not for access control.

- **A** - Signed URLs are for individual files and would require changing URLs.

- **D** - Field-Level Encryption is for securing uploaded data, not for controlling download access.

## References

- https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-choosing-signed-urls-cookies.html
- https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-signed-cookies.html
- https://tutorialsdojo.com/amazon-cloudfront/

## Domain

Design Secure Architectures
