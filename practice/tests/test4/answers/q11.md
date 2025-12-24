# Question 11

## Topic
Design Secure Architectures

## Question
A financial services organization is developing a cloud-native application on AWS to process and analyze customer transaction data. The application utilizes Amazon Aurora for the database, Amazon EFS for file storage, and Amazon EventBridge to trigger AWS Step Functions for workflow orchestration.

The organization has implemented AWS IAM Identity Center for user authentication. The data science, engineering, and compliance teams require secure access to Amazon Aurora and Amazon EFS while maintaining strict data privacy standards. The solution must adhere to the principle of least privilege and minimize administrative overhead.

Which approach best satisfies these requirements?

## Options
A. Enable the IAM Identity Center with an Identity Center directory and create permission sets for granular access for Amazon Aurora and Amazon EFS. Assign teams to groups linked to specific permission sets based on their roles.

B. Use Amazon Cognito User Pools for authentication and use Cognito Identity Pools to provide temporary AWS credentials. Create fine-grained IAM roles for Aurora and EFS access in each team.

C. Set up AWS Control Tower to manage multi-account access. Use Service Control Policies (SCPs) to restrict access to Aurora and EFS at the organizational level. Create IAM roles in each account with specific permissions.

D. Create separate AWS accounts for each team using AWS Organizations. Set up cross-account IAM roles with least privilege and assign specific Aurora and EFS permissions based on team roles.

## Correct Answer
A

## Explanation
AWS IAM Identity Center centralizes access management for various AWS accounts and applications. It provides single sign-on (SSO) access, enabling users to manage all their assigned accounts from a single location. Users can synchronize with an existing identity provider or create new users and groups directly within the service.

IAM Identity Center utilizes permission sets—collections of IAM policies—to manage user access across AWS Organizations. It includes a user-friendly AWS Access Portal for easy access to applications and supports deployment for both organization and account instances. Designed for high availability across multiple availability zones, the service ensures secure access through AWS Identity and Access Management (IAM) roles and policies.

Hence, the correct answer is: Enable the IAM Identity Center with an Identity Center directory and create permission sets for granular access for Amazon Aurora and Amazon EFS. Assign teams to groups linked to specific permission sets based on their roles. This approach provides centralized user management and granular access control and integrates well with the existing IAM Identity Center setup. This approach allows for easy assignment of permissions based on team roles and adheres to the principle of least privilege.

References:

https://aws.amazon.com/about-aws/whats-new/2023/05/amazon-sagemaker-data-wrangler-image-data-preparation/https://docs.aws.amazon.com/singlesignon/latest/userguide/get-set-up-for-idc.html

https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html

Check out this AWS Identity and Access Management Cheat Sheet:

https://tutorialsdojo.com/aws-identity-and-access-management-iam/

**Why other options are incorrect:**

- The option that says: Set up AWS Control Tower to manage multi-account access. Use Service Control Policies (SCPs) to restrict access to Aurora and EFS at the organizational level. Create IAM roles in each account with specific permissions is incorrect. AWS Control Tower is typically used for multi-account governance and high-level policy enforcement using Service Control Policies (SCPs). While SCPs can restrict access, they operate at the account or organizational level and cannot provide the fine-grained access required for individual resources like Amazon Aurora or Amazon EFS. This approach increases administrative complexity and does not minimize overhead.

- The option that says: Use Amazon Cognito User Pools for authentication and use Cognito Identity Pools to provide temporary AWS credentials. Create fine-grained IAM roles for Aurora and EFS access in each team is incorrect. Amazon Cognito typically provides user authentication and access to AWS resources through temporary credentials. However, Cognito is not inherently integrated with the IAM Identity Center, which the organization is already using. This approach introduces additional complexity and does not align with the organization's current authentication strategy.

- The option that says: Create separate AWS accounts for each team using AWS Organizations. Set up cross-account IAM roles with least privilege and assign specific Aurora and EFS permissions based on team roles is incorrect. Using separate AWS accounts and cross-account roles can enforce strict access boundaries, but it adds significant administrative overhead. Managing multiple accounts for each team is unnecessary for this scenario and does not align with the requirement to minimize complexity.

