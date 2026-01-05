# Question 30

ALBs with ACM certificates. Need notification 30 days before expiration. (Select TWO.)

## Options

A. ACM Private CA + EventBridge + Lambda + SNS.

B. EventBridge daily check DaysToExpiry metric + SNS.

C. EventBridge with AWS Health/ACM expiration events + SNS.

D. AWS Config manual rule + EventBridge + SNS.

E. Trusted Advisor + CloudWatch alarm + OpsItem.

## Correct Answer

**B. EventBridge daily check DaysToExpiry metric + SNS.**

**C. EventBridge with AWS Health/ACM expiration events + SNS.**

## Explanation

ACM certificate monitoring:
- **DaysToExpiry metric**: CloudWatch metric for certificates
- **ACM events**: Sent to EventBridge 45 days before expiry
- **AWS Health events**: Renewal state changes
- **SNS notification**: Alert administrators

### Why other options are incorrect:

- **A** - No need to modify certificates to Private CA.

- **D** - ACM has built-in managed rule; no need for manual.

- **E** - Trusted Advisor doesn't check ACM expiration.

## References

- https://docs.aws.amazon.com/acm/latest/userguide/cloudwatch-metrics.html
- https://tutorialsdojo.com/aws-certificate-manager/

## Domain

Design Secure Architectures
