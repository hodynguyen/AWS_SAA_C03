# Question 43

## Topic
Design Secure Architectures

## Question
A company is using the AWS Directory Service to integrate their on-premises Microsoft Active Directory (AD) domain with their Amazon EC2 instances via an AD connector. The below identity-based policy is attached to the IAM Identities that use the AWS Directory service:

{

"Version":"2012-10-17",

"Statement":[

{

"Sid":"DirectoryTutorialsDojo1234",

"Effect":"Allow",

"Action":[

"ds:*"

],

"Resource":"arn:aws:ds:us-east-1:987654321012:directory/d-1234567890"

},

{

"Effect":"Allow",

"Action":[

"ec2:*"

],

"Resource":"*"

}

]

}

Which of the following BEST describes what the above resource policy does?

## Options
A. Allows all AWS Directory Service (ds) calls as long as the resource contains the directory ID:  987654321012

B. Allows all AWS Directory Service (ds) calls as long as the resource contains the directory ID: DirectoryTutorialsDojo1234

C. Allows all AWS Directory Service (ds) calls as long as the resource contains the directory name of: DirectoryTutorialsDojo1234

D. Allows all AWS Directory Service (ds) calls as long as the resource contains the directory ID: d-1234567890

## Correct Answer
D

## Explanation
AWS Directory Service provides multiple ways to use Amazon Cloud Directory and Microsoft Active Directory (AD) with other AWS services. Directories store information about users, groups, and devices, and administrators use them to manage access to information and resources. AWS Directory Service provides multiple directory choices for customers who want to use existing Microsoft AD or Lightweight Directory Access Protocol (LDAP)–aware applications in the cloud. It also offers those same choices to developers who need a directory to manage users, groups, devices, and access.

Every AWS resource is owned by an AWS account, and permissions to create or access the resources are governed by permissions policies. An account administrator can attach permissions policies to IAM identities (that is, users, groups, and roles), and some services (such as AWS Lambda) also support attaching permissions policies to resources.

The following resource policy example allows all ds calls as long as the resource contains the directory ID "d-1234567890".

{

"Version":"2012-10-17",

"Statement":[

{

"Sid":"VisualEditor0",

"Effect":"Allow",

"Action":[

"ds:*"

],

"Resource":"arn:aws:ds:us-east-1:123456789012:directory/d-1234567890"

},

{

"Effect":"Allow",

"Action":[

"ec2:*"

],

"Resource":"*"

}

]

}

Hence, the correct answer is the option that says: Allows all AWS Directory Service (ds) calls as long as the resource contains the directory ID: d-1234567890.

References:

https://docs.aws.amazon.com/directoryservice/latest/admin-guide/IAM_Auth_Access_IdentityBased.html

https://docs.aws.amazon.com/directoryservice/latest/admin-guide/IAM_Auth_Access_Overview.html

Check out this AWS Identity & Access Management (IAM) Cheat Sheet:

https://tutorialsdojo.com/aws-identity-and-access-management-iam

**Why other options are incorrect:**

- The option that says: Allows all AWS Directory Service (ds) calls as long as the resource contains the directory ID: DirectoryTutorialsDojo1234 is incorrect because DirectoryTutorialsDojo1234 is the Statement ID (SID) and not the Directory ID.

- The option that says: Allows all AWS Directory Service (ds) calls as long as the resource contains the directory ID: 987654321012 is incorrect because the numbers: 987654321012 is the Account ID and not the Directory ID.

- The option that says: Allows all AWS Directory Service (ds) calls as long as the resource contains the directory name of: DirectoryTutorialsDojo1234 is incorrect because DirectoryTutorialsDojo1234 is the Statement ID (SID) and not the Directory name.

