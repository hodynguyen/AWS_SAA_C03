# Question 11

A financial services company uses Aurora, EFS, and EventBridge for a cloud-native application. They use IAM Identity Center for authentication. Data science, engineering, and compliance teams need secure access to Aurora and EFS with least privilege and minimal administrative overhead.

Which approach best satisfies these requirements?

## Options

A. Enable IAM Identity Center with an Identity Center directory. Create permission sets for granular access to Aurora and EFS. Assign teams to groups linked to specific permission sets.

B. Use Amazon Cognito User Pools for authentication and Identity Pools for temporary credentials. Create fine-grained IAM roles for each team.

C. Set up AWS Control Tower with Service Control Policies (SCPs) to restrict access at the organizational level. Create IAM roles in each account.

D. Create separate AWS accounts for each team using AWS Organizations. Set up cross-account IAM roles with specific permissions.

## Correct Answer

**A. Enable IAM Identity Center with an Identity Center directory. Create permission sets for granular access to Aurora and EFS. Assign teams to groups linked to specific permission sets.**

## Explanation

IAM Identity Center provides centralized SSO access management. Permission sets are collections of IAM policies that define access levels. By creating groups for each team and linking them to specific permission sets, you achieve granular access control with minimal overhead—all managed from a single location.

### Why other options are incorrect:

- **B** - Cognito is for application user authentication, not for AWS resource access management. It doesn't integrate with the existing IAM Identity Center setup.

- **C** - Control Tower SCPs operate at the account/OU level, not for fine-grained resource access. This adds complexity without solving the problem.

- **D** - Separate accounts add significant administrative overhead for managing team access.

## References

- https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html
- https://tutorialsdojo.com/aws-identity-and-access-management-iam/

## Domain

Design Secure Architectures
