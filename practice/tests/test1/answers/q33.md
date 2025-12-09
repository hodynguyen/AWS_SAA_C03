# Question 33

A medical records company is planning to store sensitive clinical trial data in an Amazon S3 repository with the object-level versioning feature enabled. The Solutions Architect is tasked with ensuring that no object can be overwritten or deleted by any user in a period of one year only. To meet the strict compliance requirements, the root user of the company's AWS account must also be restricted from making any changes to an object in the S3 bucket.

Which of the following is the most secure way of storing the data in S3?

## Options

A. Enable S3 Object Lock in compliance mode with a legal hold of one year.

B. Enable S3 Object Lock in governance mode with a retention period of one year.

C. Enable S3 Object Lock in compliance mode with a retention period of one year.

D. Enable S3 Object Lock in governance mode with a legal hold of one year.

## Correct Answer

**C. Enable S3 Object Lock in compliance mode with a retention period of one year.**

## Explanation

With S3 Object Lock, you can store objects using a write-once-read-many (WORM) model. Object Lock can help prevent objects from being deleted or overwritten for a fixed amount of time or indefinitely.

S3 Object Lock provides two retention modes:
- **Governance mode**: Users can't overwrite or delete an object version unless they have special permissions.
- **Compliance mode**: A protected object version can't be overwritten or deleted by any user, including the root user in your AWS account.

In compliance mode, its retention mode can't be changed, and its retention period can't be shortened.

### Why other options are incorrect:

- **B** - In governance mode, root users or users with special permissions can still modify/delete objects.

- **A & D** - You cannot set a time period for a legal hold. Legal holds remain in effect until explicitly removed.

## References

- https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock.html
- https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock-overview.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Secure Architectures
