# Question 28

A web application sends logs to CloudWatch. Certain errors can be resolved by restarting the EC2 instance.

How can you automatically restart instances when the error occurs?

## Options

A. Create CloudWatch logs metric filter, then create SNS alarm to restart instances.

B. Create Flow logs metric filter, then create CloudWatch alarm to invoke Lambda for restart.

C. Create Flow logs metric filter, then create CloudWatch alarm to restart instances.

D. Create CloudWatch logs metric filter, then create CloudWatch alarm to restart instances.

## Correct Answer

**D. Create CloudWatch logs metric filter, then create CloudWatch alarm to restart instances.**

## Explanation

CloudWatch supports automatic EC2 actions directly from alarms:
1. **Metric Filter**: Search logs for error keywords, create custom metric
2. **CloudWatch Alarm**: Monitor the metric, trigger when threshold is breached
3. **EC2 Action**: Configure alarm to automatically reboot the instance

No Lambda required—CloudWatch natively supports stop, terminate, reboot, and recover actions.

### Why other options are incorrect:

- **A** - You can't create alarms in SNS. Alarms are created in CloudWatch.

- **B, C** - VPC Flow Logs capture network traffic, not application logs.

## References

- https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/UsingAlarmActions.html
- https://tutorialsdojo.com/amazon-cloudwatch/

## Domain

Design Resilient Architectures
