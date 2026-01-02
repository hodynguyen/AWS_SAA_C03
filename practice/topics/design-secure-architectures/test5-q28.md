# Question 28

Customer PII was mistakenly uploaded to S3. The company wants to detect sensitive data and be notified if it happens again.

Which combination should be implemented? (Select TWO.)

## Options

A. Set up SQS as EventBridge target.

B. Use Amazon Macie with EventBridge rule for SensitiveData events.

C. Use AWS IoT Message Broker as EventBridge target.

D. Set up SNS topic as EventBridge target.

E. Use GuardDuty with EventBridge for CRITICAL events.

## Correct Answer

**B. Use Amazon Macie with EventBridge rule for SensitiveData events.**

**D. Set up SNS topic as EventBridge target.**

## Explanation

Solution:
- **Amazon Macie**: Discovers and classifies sensitive data (PII) in S3
- **EventBridge**: Routes Macie findings to targets
- **SNS topic**: Sends notifications (email, SMS, etc.)

### Why other options are incorrect:

- **A** - SQS is for decoupling, not notifications.

- **C** - IoT Message Broker isn't a supported EventBridge target.

- **E** - GuardDuty detects threats, not PII data classification.

## References

- https://docs.aws.amazon.com/macie/latest/user/findings-types.html
- https://tutorialsdojo.com/amazon-macie/

## Domain

Design Secure Architectures
