# Question 64

## Topic
Design Secure Architectures

## Question
A company intends to give each of its developers a personal AWS account through AWS Organizations. To enforce regulatory policies, preconfigured AWS Config rules will be set in the new accounts. A solutions architect must see to it that developers are unable to remove or modify any rules in AWS Config.

Which solution meets the objective with the least operational overhead?

## Options
A. Use an IAM Role in the new accounts with an attached IAM trust relationship to disable the access of the root user to AWS Config.

B. Add the developers' AWS account to an organization unit (OU). Attach a service control policy (SCP) to the OU that restricts access to AWS Config.

C. Configure an AWS Config rule in the root account to detect if changes to the new account’s Config rules are made.

D. Set up an AWS Control Tower in the root account to detect if there were any changes to the new account’s AWS Config rules. Attach an IAM trust relationship to the IAM User of each developer which prevents any changes in AWS Config.

## Correct Answer
B

## Explanation
Service control policies (SCPs) are a type of organization policy that you can use to manage permissions in your organization. SCPs offer central control over the maximum available permissions for all accounts in your organization. SCPs help you to ensure your accounts stay within your organization’s access control guidelines.

SCPs alone is not sufficient to grant permissions to the accounts in your organization. No permissions are granted by an SCP. An SCP defines a guardrail or sets limits on the actions that the account's administrator can delegate to the IAM users and roles in the affected accounts.

In the scenario, even if a developer has admin privileges, he/she will be unable to modify Config rules if an SCP does not permit it. You can also use SCP to block root user access. This prevents the developers from circumventing the restrictions on AWS Config access.

Therefore, the correct answer is: Add the developers' AWS account to an organization unit (OU). Attach a service control policy (SCP) to the OU that restricts access to AWS Config.

The option that says: Use an IAM Role in the new accounts with an attached IAM trust relationship to disable the access of the root user to AWS Config is incorrect. Keep in mind that the effects of IAM Policies do not apply to account root users. The "trust relationship" policy simply defines which principals can assume the IAM Role and under which conditions. Thus, this type of policy won't meet the requirement in the scenario.

The option that says: Configure an AWS Config rule in the root account to detect if changes to the new account’s Config rules are made is incorrect. This solution just monitors changes on AWS Config rules; it does not restrict permissions, which is what's needed in the scenario.

The option that says: Set up an AWS Control Tower in the root account to detect if there were any changes to the new account’s AWS Config rules. Attach an IAM trust relationship to the IAM User of each developer which prevents any changes in AWS Config is incorrect. The AWS Control Tower service is commonly used to set up and govern a secure multi-account AWS environment. This service is not used to restrict access from invoking an action to a specific resource, such as AWS Config, in your AWS account. The proper way of completing this requirement is to use a service Control Policy (SCP) and not a mere IAM Role with a trust relationship policy.

## References
- https://docs.aws.amazon.com/controltower/latest/userguide/organizations.html
- https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps.html
- https://tutorialsdojo.com/aws-organizations/
