# Question 43

A tech company that you are working for has undertaken a Total Cost Of Ownership (TCO) analysis evaluating the use of Amazon S3 versus acquiring more storage hardware. The result was that all 1200 employees would be granted access to use Amazon S3 for the storage of their personal documents.

Which of the following will you need to consider so you can set up a solution that incorporates a single sign-on feature from your corporate AD or LDAP directory and also restricts access for each individual user to a designated user folder in an S3 bucket? (Select TWO.)

## Options

A. Set up a matching IAM user for each of the 1200 users in your corporate directory.

B. Set up a Federation proxy or an Identity provider, and use AWS Security Token Service to generate temporary tokens.

C. Configure an IAM role and an IAM Policy to access the bucket.

D. Use 3rd party Single Sign-On solutions such as Atlassian Crowd, OKTA, OneLogin.

E. Map each individual user to a designated user folder in S3 using Amazon WorkDocs.

## Correct Answers

**B. Set up a Federation proxy or an Identity provider, and use AWS Security Token Service to generate temporary tokens.**

**C. Configure an IAM role and an IAM Policy to access the bucket.**

## Explanation

For enterprise identity federation with Active Directory, you can authenticate users in your organization's network and provide them access to AWS without creating new AWS identities. This is known as single sign-on (SSO). AWS STS supports SAML 2.0, which you can use with Microsoft AD FS.

### Why other options are incorrect:

- **D** - You don't need 3rd party solutions; AWS provides the necessary tools.

- **E** - There's no direct way of integrating S3 with WorkDocs for this scenario.

- **A** - Creating 1200 IAM users is unnecessary and doesn't integrate with AD/LDAP.

## References

- https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_saml.html
- https://aws.amazon.com/premiumsupport/knowledge-center/iam-s3-user-specific-folder/
- https://tutorialsdojo.com/aws-identity-and-access-management-iam/

## Domain

Design Secure Architectures
