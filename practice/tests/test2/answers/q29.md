# Question 29

A multinational company currently operates multiple AWS accounts to support its operations across various branches and business units. The company needs a more efficient and secure approach in managing its vast AWS infrastructure to avoid costly operational overhead.

Which combination of options can be used to meet the above requirements? (Select TWO.)

## Options

A. Implement AWS Organizations to create a multi-account architecture that provides a consolidated view and centralized management of AWS accounts.

B. Utilize AWS CloudTrail to enable centralized logging and monitoring across all AWS accounts.

C. Integrate AWS IAM Identity Center with the corporate directory service for centralized authentication. Configure a service control policy (SCP) to manage the AWS accounts.

D. Set up a new entity in AWS Organizations and configure its authentication system to utilize AWS Directory Service directly.

E. Establish an identity pool through Amazon Cognito and adjust the AWS IAM Identity Center settings to allow Amazon Cognito authentication.

## Correct Answers

**A. Implement AWS Organizations to create a multi-account architecture that provides a consolidated view and centralized management of AWS accounts.**

**C. Integrate AWS IAM Identity Center with the corporate directory service for centralized authentication. Configure a service control policy (SCP) to manage the AWS accounts.**

## Explanation

AWS Organizations allows you to manage multiple AWS accounts easily with consolidated billing. AWS IAM Identity Center integrates with corporate directory for centralized authentication, and SCPs enforce policies across the organization.

### Why other options are incorrect:

- **D** - Directory Service is not for multi-account authentication.

- **E** - Cognito is for external users, not corporate authentication.

- **B** - CloudTrail is for logging, not account management.

## References

- https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps.html
- https://tutorialsdojo.com/aws-organizations/

## Domain

Design Secure Architectures
