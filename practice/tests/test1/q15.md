# Question 15

A company wishes to query data that resides in multiple AWS accounts from a central data lake. Each account has its own Amazon S3 bucket that stores data unique to its business function. Access to the data lake must be granted based on user roles.

Which solution will minimize overhead and costs while meeting the required access patterns?

## Options

A. Use AWS Control Tower to centrally manage each account's S3 buckets.

B. Use AWS Lake Formation to consolidate data from multiple accounts into a single account.

C. Use Amazon Data Firehose to consolidate data from multiple accounts into a single account.

D. Create a scheduled AWS Lambda function using Amazon EventBridge for transferring data from multiple accounts to the S3 buckets of the central account.

## Correct Answer

**B. Use AWS Lake Formation to consolidate data from multiple accounts into a single account.**

## Explanation

AWS Lake Formation is a service that makes it easy to set up a secure data lake in days. A data lake is a centralized, curated, and secured repository that stores all your data, both in its original form and prepared for analysis.

Amazon S3 forms the storage layer for Lake Formation. If you already use S3, you typically begin by registering existing S3 buckets that contain your data. AWS always stores this data in your account, and only you have direct access to it.

AWS Lake Formation is integrated with AWS Glue which you can use to create a data catalog. Lake Formation lets you define policies and control data access with simple "grant and revoke permissions to data" sets at granular levels. You can assign permissions to IAM users, roles, groups, and Active Directory users using federation.

### Why other options are incorrect:

- **C** - Setting up a Data Firehose in each and every account to move data into a single location is costly and impractical. A better approach is to set up cross-account sharing with AWS Lake Formation.

- **D** - This could be done but implementation would be difficult and challenging to manage. The scenario explicitly mentioned that the solution must minimize management overhead.

- **A** - AWS Control Tower is primarily used to manage and govern multiple AWS accounts, not just S3 buckets.

## References

- https://aws.amazon.com/blogs/big-data/building-securing-and-managing-data-lakes-with-aws-lake-formation/
- https://docs.aws.amazon.com/lake-formation/latest/dg/how-it-works.html
- https://tutorialsdojo.com/aws-lake-formation/

## Domain

Design High-Performing Architectures
