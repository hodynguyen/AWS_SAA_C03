# Question 15

A media company needs to configure an S3 bucket to serve static assets for a public-facing web application.

Which methods ensure all uploaded objects can be read publicly? (Select TWO.)

## Options

A. Grant public read access to the object when uploading using the S3 Console.

B. Configure cross-origin resource sharing (CORS) to allow objects to be accessible from all domains.

C. Create an IAM role to set objects to public read.

D. Do nothing. Amazon S3 objects are already public by default.

E. Configure the S3 bucket policy to set all objects to public read.

## Correct Answer

**A. Grant public read access to the object when uploading using the S3 Console.**

**E. Configure the S3 bucket policy to set all objects to public read.**

## Explanation

S3 objects are private by default. To make objects public:
1. **Bucket policy**: Apply a policy granting `s3:GetObject` to everyone (`*`) for all objects
2. **Per-object ACL**: Set public-read permission during upload

Both approaches make objects accessible via public URLs.

### Why other options are incorrect:

- **B** - CORS allows cross-domain web requests but doesn't grant public access to objects.

- **C** - IAM roles grant permissions to AWS services/users, not public internet access.

- **D** - S3 objects are private by default, not public.

## References

- http://docs.aws.amazon.com/AmazonS3/latest/dev/s3-access-control.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Secure Architectures
