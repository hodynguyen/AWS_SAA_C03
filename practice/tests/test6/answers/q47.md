# Question 47

EC2 monitoring. Send log data to CloudWatch Logs automatically.

Which provides automated way?

## Options

A. CloudTrail Processing Library.

B. CloudTrail with log file validation.

C. AWS Transfer for SFTP.

D. CloudWatch Logs agent.

## Correct Answer

**D. CloudWatch Logs agent.**

## Explanation

CloudWatch Logs agent:
- **Automated**: Push logs to CloudWatch
- **Daemon**: Runs continuously on EC2
- **AWS CLI plugin**: Sends log data
- **Configuration**: Define log groups

### Why other options are incorrect:

- **A, B** - CloudTrail for API audit, not EC2 logs.

- **C** - SFTP for file transfer to S3.

## References

- https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/AgentReference.html
- https://tutorialsdojo.com/amazon-cloudwatch/

## Domain

Design Resilient Architectures
