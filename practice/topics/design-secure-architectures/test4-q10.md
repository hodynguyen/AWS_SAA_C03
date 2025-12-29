# Question 10

A company policy requires IAM users to have passwords with a minimum length of 12 characters. An inspection revealed some employees don't comply.

How can you automatically check whether the current password policy complies with company requirements?

## Options

A. Create an Amazon CloudWatch event rule matching IAM "ChangePassword" events. Use SNS for notifications.

B. Create a CloudTrail trail. Filter by Event Name "ChangePassword" to list users who changed passwords.

C. Create a Scheduled Lambda Function running a custom script to check compliance periodically.

D. Configure AWS Config to trigger an evaluation that checks password policy compliance periodically.

## Correct Answer

**D. Configure AWS Config to trigger an evaluation that checks password policy compliance periodically.**

## Explanation

AWS Config continuously monitors and records AWS resource configurations. The `IAM_PASSWORD_POLICY` managed rule automatically evaluates whether your account's password policy meets compliance requirements (minimum length, complexity, etc.). Config provides a compliance dashboard without custom code.

### Why other options are incorrect:

- **A** - CloudWatch Events/EventBridge monitors events, not configuration compliance. It can't check password policy settings.

- **B** - CloudTrail logs API calls but doesn't evaluate policy compliance.

- **C** - Lambda scripts work but require custom development. AWS Config provides this functionality out-of-box.

## References

- https://docs.aws.amazon.com/config/latest/developerguide/iam-password-policy.html
- https://tutorialsdojo.com/aws-config/

## Domain

Design Secure Architectures
