# Question 42

## Topic
Design Secure Architectures

## Question
A company uses multiple AWS accounts consolidated under AWS Organizations. The company needs to copy multiple Amazon S3 objects to an S3 bucket in a different owned AWS account. The Solutions Architect must configure permissions to enable this transfer while ensuring the destination account owns the copied objects rather than the source account.

How can the Architect accomplish this requirement?

## Options
A. Set up cross-origin resource sharing (CORS) in S3 by creating a bucket policy that includes AmazonS3FullAccess and allows an IAM user or role to copy objects.

B. Configure cross-account permissions in S3 by creating an IAM customer-managed policy that allows an IAM user or role to copy objects from the source bucket to the destination bucket. Then attach the policy to the IAM user or role.

C. Connect the two S3 buckets from two different AWS accounts to Amazon WorkDocs. Set up cross-account access to integrate the two S3 buckets.

D. Enable the Requester Pays feature in the source S3 bucket.

## Correct Answer
B

## Explanation
By default, an S3 object is owned by the account that uploaded the object. Granting the destination account the permissions to perform the cross-account copy makes sure that the destination owns the copied objects.

To be sure a destination account owns an S3 object copied from another account:
- Attach a bucket policy to the source bucket in Account A
- Attach an IAM policy to a user or role in Account B
- Use the IAM user or role in Account B to perform the cross-account copy

**Why other options are incorrect:**
- **Option A** is incorrect because CORS is for client web applications in different domains.
- **Option C** is incorrect because WorkDocs can't directly integrate S3 buckets from different accounts.
- **Option D** is incorrect because Requester Pays is about billing, not object ownership.

## References
- https://docs.aws.amazon.com/AmazonS3/latest/dev/example-walkthroughs-managing-access-example2.html
- https://aws.amazon.com/premiumsupport/knowledge-center/copy-s3-objects-account/
- https://tutorialsdojo.com/amazon-s3/
