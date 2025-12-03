# Question 21

A telecommunications company is planning to grant AWS Console access to its developers. Company policy requires the use of identity federation and role-based access control. Currently, the roles are already assigned via groups in the corporate Active Directory.

In this scenario, what combination of the following services can provide developers access to the AWS console? (Select TWO.)

## Options

A. IAM Groups

B. AWS Directory Service Simple AD

C. AWS Directory Service AD Connector

D. AWS Lambda

E. IAM Roles

## Correct Answers

**C. AWS Directory Service AD Connector**

**E. IAM Roles**

## Explanation

AWS Directory Service provides multiple ways to use Amazon Cloud Directory and Microsoft Active Directory (AD) with other AWS services. Directories store information about users, groups, and devices, and administrators use them to manage access to information and resources.

Considering that the company is using a corporate Active Directory, it is best to use AWS Directory Service AD Connector for easier integration. In addition, since the roles are already assigned using groups in the corporate Active Directory, it would be better to also use IAM Roles. You can assign an IAM Role to the users or groups from your Active Directory once it is integrated with your VPC via the AWS Directory Service AD Connector.

### Why other options are incorrect:

- **B** - AWS Directory Service Simple AD only provides a subset of the features offered by AWS Managed Microsoft AD. AD Connector is more suitable since it's a directory gateway to redirect requests to your on-premises Microsoft Active Directory.

- **A** - IAM Groups is just a collection of IAM users. In this scenario, IAM Roles is more suitable for permissions to create AWS Directory Service resources.

- **D** - AWS Lambda is primarily used for serverless computing.

## References

- https://aws.amazon.com/blogs/security/how-to-connect-your-on-premises-active-directory-to-aws-using-ad-connector/
- https://docs.aws.amazon.com/directoryservice/latest/admin-guide/ad_connector_getting_started.html
- https://tutorialsdojo.com/aws-directory-service/

## Domain

Design Resilient Architectures
