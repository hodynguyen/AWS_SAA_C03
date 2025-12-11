# Question 16

A company needs to assess and audit all the configurations in its AWS account. It must enforce strict compliance by tracking all configuration changes made to any of its Amazon S3 buckets. Publicly accessible S3 buckets should also be identified automatically to avoid data breaches.

Which of the following options will meet this requirement?

## Options

A. Use AWS Config to set up a rule in your AWS account.

B. Use AWS IAM to generate a credential report.

C. Use AWS CloudTrail and review the event history of your AWS account.

D. Use AWS Trusted Advisor to analyze your AWS environment.

## Correct Answer

**A. Use AWS Config to set up a rule in your AWS account.**

## Explanation

AWS Config is a service that enables you to assess, audit, and evaluate the configurations of your AWS resources. Config continuously monitors and records your AWS resource configurations.

By creating an AWS Config rule, you can enforce your ideal configuration in your AWS account and check if resources comply with your desired configurations.

### Why other options are incorrect:

- **D** - Trusted Advisor provides best practice recommendations, not enforcement.

- **B** - IAM credential report lists IAM users, not resource configurations.

- **C** - CloudTrail tracks API calls but doesn't enforce rules.

## References

- https://aws.amazon.com/config/
- https://tutorialsdojo.com/aws-config/

## Domain

Design Secure Architectures
