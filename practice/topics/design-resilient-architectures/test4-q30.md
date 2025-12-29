# Question 30

A company wants to get notified of upcoming AWS events that may affect their EC2 instances.

What is the recommended solution?

## Options

A. Create EventBridge rule scheduled every 24 hours. Lambda checks Service Health Dashboard.

B. Create EventBridge rule for Service Health Dashboard events. Send to SNS.

C. Create EventBridge rule for Personal Health Dashboard events. Send to SNS.

D. Create EventBridge rule for EC2 status changes. Lambda sends notification and restarts instances.

## Correct Answer

**C. Create EventBridge rule for Personal Health Dashboard events. Send to SNS.**

## Explanation

AWS Personal Health Dashboard provides account-specific events about AWS resources:
- Scheduled maintenance
- Instance retirement notifications
- Service disruptions affecting your resources

EventBridge can capture these events and trigger SNS notifications automatically.

### Why other options are incorrect:

- **A, B** - Service Health Dashboard shows public AWS-wide events, not account-specific resources.

- **D** - This reacts after instances stop, not before (for scheduled events).

## References

- https://docs.aws.amazon.com/health/latest/ug/cloudwatch-events-health.html
- https://tutorialsdojo.com/aws-health/

## Domain

Design Resilient Architectures
