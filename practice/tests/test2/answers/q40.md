# Question 40

A company wants to streamline the process of creating multiple AWS accounts within an AWS Organization. Each organization unit (OU) must be able to launch new accounts with preapproved configurations from the security team.

Which solution entails the least amount of effort to implement?

## Options

A. Centralized the creation of AWS accounts using AWS Systems Manager OpsCenter. Enforce policies using AWS Security Hub.

B. Configure AWS Resource Access Manager (AWS RAM) to launch new AWS accounts.

C. Set up an AWS Config aggregator on the root account of the organization to enable multi-account data aggregation.

D. Set up an AWS Control Tower Landing Zone. Enable pre-packaged guardrails to enforce policies or detect violations.

## Correct Answer

**D. Set up an AWS Control Tower Landing Zone. Enable pre-packaged guardrails to enforce policies or detect violations.**

## Explanation

AWS Control Tower provides a single location to set up a well-architected multi-account environment with governance guardrails. It offers Account Factory for automated account creation.

### Why other options are incorrect:

- **B** - RAM is for resource sharing, not account creation.

- **C** - Config aggregator is for compliance monitoring.

- **A** - Systems Manager OpsCenter is for operational issues.

## References

- https://docs.aws.amazon.com/controltower/latest/userguide/account-factory.html
- https://aws.amazon.com/controltower/

## Domain

Design Secure Architectures
