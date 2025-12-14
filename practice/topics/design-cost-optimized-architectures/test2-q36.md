# Question 36

An organization is currently using a tape backup solution to store its application data on-premises. Plans are in place to use a cloud storage service to preserve the backup data for up to 10 years, which may be accessed about once or twice a year.

Which of the following is the most cost-effective option to implement this solution?

## Options

A. Use Amazon S3 to store the backup data and add a lifecycle rule to transition the current version to Amazon S3 Glacier.

B. Use AWS Storage Gateway to backup the data directly to Amazon S3 Glacier Flexible Retrieval.

C. Use AWS Storage Gateway to backup the data and transition it to Amazon S3 Glacier Deep Archive.

D. Order an AWS Snowball Edge appliance to import the backup directly to Amazon S3 Glacier Flexible Retrieval.

## Correct Answer

**C. Use AWS Storage Gateway to backup the data and transition it to Amazon S3 Glacier Deep Archive.**

## Explanation

Tape Gateway can transition virtual tapes to Amazon S3 Glacier Deep Archive storage class, enabling you to reduce monthly storage costs by up to 75% for long-term data.

### Why other options are incorrect:

- **B** - Glacier Flexible Retrieval is more expensive than Deep Archive.

- **D** - Snowball can't directly integrate with Glacier.

- **A** - S3 lifecycle is valid but Storage Gateway is better for tape.

## References

- https://aws.amazon.com/storagegateway/faqs/
- https://tutorialsdojo.com/aws-storage-gateway/

## Domain

Design Cost-Optimized Architectures
