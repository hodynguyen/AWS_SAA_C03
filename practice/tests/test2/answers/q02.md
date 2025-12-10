# Question 2

A company has a top priority requirement to monitor certain database metrics and send email notifications to the Operations team if any issues occur.

Which combination of AWS services can accomplish this requirement? (Select TWO.)

## Options

A. Amazon Simple Notification Service (SNS)

B. Amazon CloudWatch

C. Amazon Simple Queue Service (SQS)

D. Amazon EC2 Instance with a running Berkeley Internet Name Domain (BIND) Server

E. Amazon Simple Email Service

## Correct Answers

**A. Amazon Simple Notification Service (SNS)**

**B. Amazon CloudWatch**

## Explanation

Amazon CloudWatch and Amazon Simple Notification Service (SNS) are correct. You can use Amazon CloudWatch to monitor the database and then Amazon SNS to send the emails to the Operations team.

CloudWatch collects monitoring and operational data in the form of logs, metrics, and events, providing you with a unified view of AWS resources, applications, and services.

SNS is a highly available, durable, secure, fully managed pub/sub messaging service that enables you to decouple microservices, distributed systems, and serverless applications.

### Why other options are incorrect:

- **E** - SES is primarily for bulk emails and marketing, not system notifications.

- **C** - SQS is for message queuing, not monitoring or notifications.

- **D** - BIND is for DNS services, not monitoring.

## References

- https://aws.amazon.com/cloudwatch/
- https://aws.amazon.com/sns/
- https://tutorialsdojo.com/amazon-cloudwatch/

## Domain

Design Resilient Architectures
