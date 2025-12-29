# Question 9

A company must integrate on-premises LDAP directory service with AWS IAM for VPC access. The identity store is NOT compatible with SAML.

Which approach provides a valid integration solution?

## Options

A. Use IAM roles to rotate IAM credentials whenever LDAP credentials are updated.

B. Use AWS IAM Identity Center to manage access between AWS and your LDAP.

C. Use an IAM policy that references the LDAP identifiers and AWS credentials.

D. Develop an on-premises custom identity broker application and use STS to issue short-lived AWS credentials.

## Correct Answer

**D. Develop an on-premises custom identity broker application and use STS to issue short-lived AWS credentials.**

## Explanation

When your identity store doesn't support SAML 2.0, you build a custom identity broker. The broker authenticates users against LDAP, then calls STS (AssumeRole or GetFederationToken) to obtain temporary AWS credentials. Users receive short-lived credentials for AWS access.

### Why other options are incorrect:

- **A** - Manual credential rotation doesn't provide federation or integrate LDAP with IAM.

- **B** - IAM Identity Center requires SAML 2.0-compatible identity providers.

- **C** - IAM policies can't directly reference LDAP identifiers for authentication.

## References

- https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_common-scenarios_federated-users.html
- https://tutorialsdojo.com/aws-identity-and-access-management-iam/

## Domain

Design Secure Architectures
