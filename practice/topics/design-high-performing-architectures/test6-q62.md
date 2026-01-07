# Question 62

Multiple divisions, multiple accounts. IT governance and cost oversight while divisions maintain control. (Select TWO.)

## Options

A. Separate VPCs + Transit Gateway.

B. Separate AZs + Global Accelerator.

C. IAM cross-account access.

D. Trusted Advisor + Tag Editor.

E. AWS Organizations + Consolidated Billing.

## Correct Answer

**C. IAM cross-account access.**

**E. AWS Organizations + Consolidated Billing.**

## Explanation

Multi-account governance:
- **IAM cross-account**: Centralized IT admin access
- **Consolidated Billing**: Single invoice, cost overview
- **AWS Organizations**: Hierarchical account management
- **Division autonomy**: Each has own account

### Why other options are incorrect:

- **A** - VPCs for network, not account management.

- **B** - AZs for HA, not governance.

- **D** - Trusted Advisor for best practices, not governance.

## References

- http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/consolidated-billing.html
- https://tutorialsdojo.com/aws-billing-and-cost-management/

## Domain

Design High-Performing Architectures
