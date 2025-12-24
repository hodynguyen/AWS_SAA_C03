# Question 10

## Topic
Design Secure Architectures

## Question
A new company policy requires IAM users to change their passwords’ minimum length to 12 characters. After a random inspection, you found out that there are still employees who do not follow the policy.

How can you automatically check and evaluate whether the current password policy for an account complies with the company password policy?

## Options
A. Create a rule in the Amazon CloudWatch event. Build an event pattern to match events on IAM. Set the event name to “ChangePassword” in the event pattern. Configure SNS to send notifications to you whenever a user has made changes to his password.

B. Create a CloudTrail trail. Filter the result by setting the attribute to “Event Name” and lookup value to “ChangePassword”. This easily gives you the list of users who have made changes to their passwords.

C. Create a Scheduled Lambda Function that will run a custom script to check compliance against changes made to the passwords periodically.

D. Configure AWS Config to trigger an evaluation that will check the compliance for a user’s password periodically.

## Correct Answer
D

## Explanation
AWS Config is a service that enables you to assess, audit, and evaluate the configurations of your AWS resources. Config continuously monitors and records your AWS resource configurations and allows you to automate the evaluation of recorded configurations against desired configurations.

In the scenario given, we can utilize AWS Config to check for compliance on the password policy by configuring the Config rule to check the IAM_PASSWORD_POLICY on an account. Additionally, because Config integrates with AWS Organizations, we can improve the setup to aggregate compliance information across accounts to a central dashboard.

Hence, the correct answer is: Configure AWS Config to trigger an evaluation that will check the compliance for a user’s password periodically.

Create a CloudTrail trail. Filter the result by setting the attribute to “Event Name” and lookup value to “ChangePassword”. This easily gives you the list of users who have made changes to their passwords is incorrect because this setup will just give you the name of the users who have made changes to their respective passwords. It will not give you the ability to check whether their passwords have met the required minimum length.

Create a Scheduled Lambda function that will run a custom script to check compliance against changes made to the passwords periodically is a valid solution but still incorrect. AWS Config is already integrated with AWS Lambda. You don't have to create and manage your own Lambda function. You just have to define a Config rule where you will check compliance, and Lambda will process the evaluation. Moreover, you can't directly create a scheduled function by using Lambda itself. You have to create a rule in AWS CloudWatch Events to run the Lambda functions on the schedule that you define.

Create a rule in the Amazon CloudWatch event. Build an event pattern to match events on IAM. Set the event name to “ChangePassword” in the event pattern. Configure SNS to send notifications to you whenever a user has made changes to his password is incorrect because this setup will just alert you whenever a user changes his password. Sure, you’ll have information about who made changes, but that is not enough to check whether it complies with the required minimum password length. This can be easily done in AWS Config.

References:

https://docs.aws.amazon.com/config/latest/developerguide/evaluate-config-rules.html

https://aws.amazon.com/config/

Check out this AWS Config Cheat Sheet:

https://tutorialsdojo.com/aws-config/


