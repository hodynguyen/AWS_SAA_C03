# Question 24

Developers use IAM access keys for automation. The security team needs to automatically deactivate and delete keys older than 90 days with minimal effort.

Which solution meets these requirements?

## Options

A. Use AWS Config managed rule to check key rotation. Create EventBridge rule for non-compliant keys. Invoke Lambda to deactivate and delete.

B. Create EventBridge rule to filter keys older than 90 days. Schedule AWS Batch job every 24 hours to delete keys.

C. Create custom AWS Config rule for key max-age. Use EventBridge Scheduler to invoke AWS Batch every 24 hours.

D. Create EventBridge rule to filter keys older than 90 days. Invoke Lambda to deactivate and delete old keys.

## Correct Answer

**A. Use AWS Config managed rule to check key rotation. Create EventBridge rule for non-compliant keys. Invoke Lambda to deactivate and delete.**

## Explanation

AWS Config has a managed rule `access-keys-rotated` that checks if IAM access keys are rotated within a specified period. When Config detects non-compliance:
1. **EventBridge** captures the compliance change event
2. **Lambda** is triggered to deactivate and delete the old keys

This uses managed services with minimal custom code.

### Why other options are incorrect:

- **B, D** - EventBridge cannot directly filter IAM keys by age. Config is needed for compliance evaluation.

- **C** - Custom Config rules add unnecessary complexity when a managed rule exists.

## References

- https://aws.amazon.com/blogs/mt/managing-aged-access-keys-through-aws-config-remediations/
- https://tutorialsdojo.com/aws-config/

## Domain

Design Secure Architectures
