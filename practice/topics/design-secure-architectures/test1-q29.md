# Question 29

A newly hired Solutions Architect is assigned to manage a set of CloudFormation templates that are used in the company's cloud architecture in AWS. The Architect accessed the templates and tried to analyze the configured IAM policy for an S3 bucket.

```json
{ 
 "Version": "2012-10-17", 
 "Statement": [ 
  { 
   "Effect": "Allow", 
   "Action": [ 
    "s3:Get*", 
    "s3:List*" 
   ], 
   "Resource": "*" 
  }, 
  { 
   "Effect": "Allow", 
   "Action": "s3:PutObject", 
   "Resource": "arn:aws:s3:::boracay/*" 
  } 
 ] 
}
```

What does the above IAM policy allow? (Select THREE.)

## Options

A. An IAM user with this IAM policy is allowed to read objects from all S3 buckets owned by the account.

B. An IAM user with this IAM policy is allowed to read objects in the boracay S3 bucket but not allowed to list the objects in the bucket.

C. An IAM user with this IAM policy is allowed to change access rights for the boracay S3 bucket.

D. An IAM user with this IAM policy is allowed to write objects into the boracay S3 bucket.

E. An IAM user with this IAM policy is allowed to read objects from the boracay S3 bucket.

F. An IAM user with this IAM policy is allowed to read and delete objects from the boracay S3 bucket.

## Correct Answers

**A. An IAM user with this IAM policy is allowed to read objects from all S3 buckets owned by the account.**

**D. An IAM user with this IAM policy is allowed to write objects into the boracay S3 bucket.**

**E. An IAM user with this IAM policy is allowed to read objects from the boracay S3 bucket.**

## Explanation

Based on the provided IAM policy, the user is only allowed to get, write, and list all of the objects for the boracay s3 bucket. The s3:PutObject basically means that you can submit a PUT object request to the S3 bucket to store data.

The first statement allows s3:Get* and s3:List* on all resources (*), which means reading and listing from all S3 buckets. The second statement allows s3:PutObject only on the boracay bucket.

### Why other options are incorrect:

- **C** - The template does not have any statements which allow the user to change access rights in the bucket.

- **B** - There is a s3:List* which permits the user to list objects.

- **F** - Although you can read objects from the bucket, you cannot delete any objects (no s3:Delete* permission).

## References

- https://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectOps.html
- https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Secure Architectures
