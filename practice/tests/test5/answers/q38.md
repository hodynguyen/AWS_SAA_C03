# Question 38

Multiple departments deploy resources to AWS. The company wants to track service quota usage to avoid unexpected limits.

Which combination should be implemented? (Select TWO.)

## Options

A. EventBridge with SNS topic as notification target.

B. Query Trusted Advisor every 24 hours with Developer support plan.

C. Create SNS topic as target for notifications.

D. Use AWS Config managed rule with Lambda.

E. Lambda function to refresh Trusted Advisor Service Limits every 24 hours.

## Correct Answer

**A. EventBridge with SNS topic as notification target.**

**E. Lambda function to refresh Trusted Advisor Service Limits every 24 hours.**

## Explanation

Quota monitoring pattern:
1. **Lambda refreshes Trusted Advisor**: Gets latest quota data
2. **EventBridge captures events**: Routes status changes
3. **SNS sends notifications**: Alerts when nearing limits

### Why other options are incorrect:

- **B** - DescribeTrustedAdvisorChecks returns all checks; requires Business+ plan for API access.

- **C** - Incomplete; needs event source like EventBridge.

- **D** - Config is for compliance, not quota monitoring.

## References

- https://aws.amazon.com/solutions/implementations/quota-monitor/
- https://tutorialsdojo.com/aws-trusted-advisor/

## Domain

Design High-Performing Architectures
