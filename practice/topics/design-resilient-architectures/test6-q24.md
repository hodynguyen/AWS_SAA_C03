# Question 24

Node.js app on Elastic Beanstalk. DevOps team needs application log files.

Where does Beanstalk store app and server log files?

## Options

A. S3 for app files, Glacier or CloudWatch Logs for server logs.

B. S3 for app files, only EBS volumes for server logs.

C. S3 for app files, CloudTrail or CloudWatch Logs for server logs.

D. S3 for app files, S3 or CloudWatch Logs for server logs.

## Correct Answer

**D. S3 for app files, S3 or CloudWatch Logs for server logs.**

## Explanation

Elastic Beanstalk storage:
- **App files**: Stored in S3 automatically
- **Server logs**: S3 or CloudWatch Logs (optional)
- **CloudWatch Logs agent**: Publishes to CloudWatch
- **Environment config**: Enable log streaming

### Why other options are incorrect:

- **A** - Glacier is archive, not direct log storage.

- **B** - Server logs can also go to S3/CloudWatch.

- **C** - CloudTrail is for API auditing, not app logs.

## References

- https://aws.amazon.com/elasticbeanstalk/faqs/
- https://tutorialsdojo.com/aws-elastic-beanstalk/

## Domain

Design Resilient Architectures
