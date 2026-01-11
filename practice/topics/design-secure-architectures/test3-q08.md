# Question 8

## Topic
Design Secure Architectures

## Question
A company that is rapidly growing in recent months has been in the process of setting up IAM users on its single AWS Account. A solutions architect has been tasked to handle the user management, which includes granting read-only access to users and denying permissions whenever an IAM user has no MFA setup. New users will be added frequently based on their respective departments.

Which of the following action is the MOST secure way to grant permissions to the new users?

## Options
A. Create a Service Control Policy (SCP) that enforces MFA authentication for each department. Add a trust relationship to every SCP and attach it to each IAM User.

B. Set up IAM roles for each IAM user and associate a permissions boundary that defines the maximum permissions.

C. Create an IAM Role that enforces MFA authentication with the least privilege permission. Set up a corresponding IAM Group for each department. Attach the IAM Role to the IAM Groups.

D. Launch an IAM Group for each department. Create an IAM Policy that enforces MFA authentication with the least privilege permission. Attach the IAM Policy to each IAM Group.

## Correct Answer
D

## Explanation
An IAM user group is a collection of IAM users. User groups let you specify permissions for multiple users, which can make it easier to manage the permissions for those users.

You can attach an identity-based policy to a user group so that all of the users in the user group receive the policy's permissions. The IAM Policy that enforces MFA authentication can then be attached to an IAM Group to quickly apply to all IAM Users.

**Why other options are incorrect:**
- **Option A** is incorrect because an SCP can only be attached to the organization root, to an OU, or directly to an account, not to IAM Users. The scenario uses a single AWS account.
- **Option B** is incorrect because permissions boundaries define maximum permissions, not the recommended least privilege approach.
- **Option C** is incorrect because there is no direct way to assign an IAM Role to an IAM Group.

## References
- https://aws.amazon.com/iam/features/mfa/
- https://aws.amazon.com/premiumsupport/knowledge-center/mfa-iam-user-aws-cli/
- https://tutorialsdojo.com/aws-identity-and-access-management-iam/
