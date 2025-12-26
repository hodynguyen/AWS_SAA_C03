# Question 30

## Topic
Design Resilient Architectures

## Question
A company has a fixed set of Amazon EC2 instances inside a VPC in the AWS cloud. The instances run a mission-critical application. In a recent incident, one of the EC2 instances suddenly powered down which affected the availability of the application. To avoid this incident in the future, the management wants to get notified of any upcoming AWS events that may affect these EC2 instances.

Which of the following options is the recommended action to meet the above requirements?

## Options
A. Create an Amazon EventBridge (Amazon CloudWatch Events) rule that is scheduled to run every 24 hours. Set the target to an AWS Lambda function that will check AWS Service Health Dashboard and send notifications for any events that may affect Amazon EC2 instances.

B. Set up an Amazon EventBridge (Amazon CloudWatch Events) rule to check for AWS Service Health Dashboard events that are related to Amazon EC2 instances. To send notifications, set an Amazon SNS topic as a target for the rule.

C. Create an Amazon EventBridge (Amazon CloudWatch Events) rule to check for AWS Personal Health Dashboard events that are related to Amazon EC2 instances. To send notifications, set an Amazon SNS topic as a target for the rule.

D. Set up an Amazon EventBridge (Amazon CloudWatch Events) rule to check for any status change for Amazon EC2 instances. Set the target to an AWS Lambda function that will send a notification and restart the affected Amazon EC2 instances.

## Correct Answer
C

## Explanation
AWS Health provides ongoing visibility into your resource performance and the availability of your AWS services and accounts. You can use AWS Health events to learn how service and resource changes might affect your applications running on AWS. AWS Health provides relevant and timely information to help you manage events in progress. AWS Health also helps you be aware of and to prepare for planned activities.

You can use Amazon EventBridge to detect and react to AWS Health events. Then, based on the rules that you create, EventBridge invokes one or more target actions when an event matches the values that you specify in a rule. For example, you can use AWS Health to receive email notifications if you have AWS resources in your AWS account that are scheduled for updates, such as Amazon Elastic Compute Cloud (Amazon EC2) instances.

Your account events – This page shows events that are specific to your account. You can view open, recent, and scheduled changes. You can also view notifications, as well as an event log that shows all events from the past 90 days.

Therefore, the correct answer is: Create an Amazon EventBridge (Amazon CloudWatch Events) rule to check for AWS Personal Health Dashboard events that are related to Amazon EC2 instances. To send notifications, set an Amazon SNS topic as a target for the rule. You can use Amazon EventBridge to detect and react to AWS Health events and then send messages using AWS SNS.

References:

https://docs.aws.amazon.com/health/latest/ug/cloudwatch-events-health.html

https://docs.aws.amazon.com/health/latest/ug/what-is-aws-health.html

https://docs.aws.amazon.com/health/latest/ug/getting-started-health-dashboard.html

Check out these Amazon CloudWatch and AWS Health Cheat Sheets:

https://tutorialsdojo.com/amazon-cloudwatch/

https://tutorialsdojo.com/aws-health/

**Why other options are incorrect:**

- The option that says: Create an Amazon EventBridge (Amazon CloudWatch Events) rule that is scheduled to run every 24 hours. Set the target to an AWS Lambda function that will check AWS Service Health Dashboard and send notifications for any events that may affect Amazon EC2 instances is incorrect. First of all, the AWS Service Health Dashboard doesn't show events related to specific EC2 instances on individual accounts. This service shows the public events that may affect several customers in particular regions.

- The option that says: Set up an Amazon EventBridge (Amazon CloudWatch Events) rule to check for any status change for Amazon EC2 instances. Set the target to an AWS Lambda function that will send a notification and restart the affected Amazon EC2 instances is incorrect. Take note that the requirement is to send notifications for upcoming or scheduled AWS events. This solution will send notifications after the EC2 instances have stopped and not show upcoming events in AWS.

- The option that says: Set up an Amazon EventBridge (Amazon CloudWatch Events) rule to check for AWS Service Health Dashboard events that are related to Amazon EC2 instances. To send notifications, set an Amazon SNS topic as a target for the rule is incorrect. AWS Service Health Dashboard shows public events that may affect several customers in particular regions. It doesn't show events related to specific EC2 instances on individual AWS accounts. You have to check the events on the AWS Personal Health Dashboard instead.

