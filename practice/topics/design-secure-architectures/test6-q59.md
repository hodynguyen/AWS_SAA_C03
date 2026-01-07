# Question 59

S3 bucket shared with external users. Bucket owner needs full access to all uploaded objects.

What action?

## Options

A. Create CORS configuration.

B. Enable server access logging + IAM policy.

C. Create bucket policy requiring bucket-owner-full-control.

D. Enable Requester Pays.

## Correct Answer

**C. Create bucket policy requiring bucket-owner-full-control.**

## Explanation

S3 object ownership:
- **Uploaded by others**: Owner is uploader
- **bucket-owner-full-control**: Grant access to bucket owner
- **Bucket policy**: Require this ACL on PUT
- **Cross-account**: Common pattern

### Why other options are incorrect:

- **A** - CORS for cross-origin web requests.

- **B** - Logging doesn't grant access.

- **D** - Requester Pays is about billing.

## References

- https://aws.amazon.com/premiumsupport/knowledge-center/s3-bucket-owner-access/
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Secure Architectures
