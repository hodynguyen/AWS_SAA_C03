# Question 6

A startup needs to set up a secure, compliant, multi-account AWS environment. They require a dashboard for continuous detection of policy non-conformance and non-compliant resources.

Which solution provides the easiest way to fulfill this requirement?

## Options

A. Launch new AWS member accounts using AWS CloudFormation StackSets. Use AWS Config to track configuration changes. Set up a Multi-Account Data Aggregator.

B. Use AWS Control Tower to launch a landing zone to automatically provision accounts through Account Factory. Utilize the Control Tower dashboard to monitor accounts. Set up preventive and detective guardrails.

C. Use AWS Organizations to build a landing zone. Utilize AWS Personal Health Dashboard to see accounts. Enable guardrails for policy enforcement.

D. Use AWS Service Catalog to launch new accounts. Configure Launch Constraints to track configuration changes. Set up a Data Aggregator.

## Correct Answer

**B. Use AWS Control Tower to launch a landing zone to automatically provision accounts through Account Factory. Utilize the Control Tower dashboard to monitor accounts. Set up preventive and detective guardrails.**

## Explanation

AWS Control Tower provides a turnkey solution for multi-account governance. It orchestrates Organizations, Service Catalog, and SSO to create a landing zone. The built-in dashboard shows policy compliance status across all accounts, and guardrails enforce preventive and detective controls automatically.

### Why other options are incorrect:

- **A** - CloudFormation StackSets + Config works but requires significant manual setup and configuration overhead.

- **C** - AWS Organizations doesn't have a built-in compliance dashboard. Personal Health Dashboard shows AWS service issues, not account compliance.

- **D** - Service Catalog manages IT service catalogs, not compliance detection or account provisioning.

## References

- https://docs.aws.amazon.com/controltower/latest/userguide/what-is-control-tower.html
- https://tutorialsdojo.com/aws-control-tower/

## Domain

Design Secure Architectures
