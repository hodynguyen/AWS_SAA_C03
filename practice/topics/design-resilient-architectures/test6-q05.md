# Question 5

Multinational company with multiple AWS accounts per department. Need centralized access control to comply with security policy.

Which is the most suitable way to set up multi-account environment?

## Options

A. Cross-account access with IAM policies per department.

B. Identity Federation with IAM roles.

C. AWS Organizations with Service Control Policies.

D. Common IAM policy across all accounts.

## Correct Answer

**C. AWS Organizations with Service Control Policies.**

## Explanation

AWS Organizations + SCPs:
- **Centralized management**: Single pane of glass
- **SCPs**: Control what services/actions are allowed per account
- **Hierarchical**: Apply policies to OUs
- **Account creation**: Automate new account provisioning

### Why other options are incorrect:

- **A** - Cross-account access doesn't scale for many accounts.

- **B** - Federation is for authentication, not policy management.

- **D** - Can't create common IAM policy across accounts.

## References

- https://aws.amazon.com/organizations/
- https://tutorialsdojo.com/aws-organizations/

## Domain

Design Resilient Architectures
