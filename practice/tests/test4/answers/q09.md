# Question 9

## Topic
Design Secure Architectures

## Question
A company must integrate the Lightweight Directory Access Protocol (LDAP) directory service from the on-premises data center to the AWS VPC using IAM. The identity store which is currently being used is not compatible with SAML.

Which of the following provides the most valid approach to implement the integration?

## Options
A. Use IAM roles to rotate the IAM credentials whenever LDAP credentials are updated.

B. Use AWS IAM Identity Center to manage access between AWS and your LDAP.

C. Use an IAM policy that references the LDAP identifiers and AWS credentials.

D. Develop an on-premises custom identity broker application and use STS to issue short-lived AWS credentials.

## Correct Answer
D

## Explanation
If your identity store is not compatible with SAML 2.0 then you can build a custom identity broker application to perform a similar function. The broker application authenticates users, requests temporary credentials for users from AWS, and then provides them to the user to access AWS resources.

The application verifies that employees are signed into the existing corporate network's identity and authentication system, which might use LDAP, Active Directory, or another system. The identity broker application then obtains temporary security credentials for the employees.

To get temporary security credentials, the identity broker application calls either AssumeRole or GetFederationToken to obtain temporary security credentials, depending on how you want to manage the policies for users and when the temporary credentials should expire. The call returns temporary security credentials consisting of an AWS access key ID, a secret access key, and a session token. The identity broker application makes these temporary security credentials available to the internal company application. The app can then use the temporary credentials to make calls to AWS directly. The app caches the credentials until they expire, and then requests a new set of temporary credentials.

Hence, the correct answer is: Develop an on-premises custom identity broker application and use STS to issue short-lived AWS credentials.

References:

https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_common-scenarios_federated-users.html

https://aws.amazon.com/blogs/aws/aws-identity-and-access-management-now-with-identity-federation/

Tutorials Dojo's AWS Certified Solutions Architect Associate Exam Study Guide:

https://tutorialsdojo.com/aws-certified-solutions-architect-associate/

Check out this AWS Identity and Access Management Cheat Sheet:

https://tutorialsdojo.com/aws-identity-and-access-management-iam/

**Why other options are incorrect:**

- The option that says: Use an IAM policy that references the LDAP identifiers and AWS credentials is incorrect because simply using an IAM policy is not enough to integrate your LDAP service to IAM. You need to use SAML, STS, or a custom identity broker.

- The option that says: Use AWS IAM Identity Center to manage access between AWS and your LDAP is incorrect. While AWS IAM Identity Center can integrate with external identity providers, it primarily supports SAML 2.0-based identity providers. The question explicitly states that the identity store is not compatible with SAML.

- The option that says: Use IAM roles to rotate the IAM credentials whenever LDAP credentials are updated is incorrect because manually rotating the IAM credentials is not an optimal solution to integrate your on-premises and VPC network. You need to use SAML, STS, or a custom identity broker.

