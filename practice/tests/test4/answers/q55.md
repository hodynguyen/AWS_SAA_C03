# Question 55

## Topic
Design Resilient Architectures

## Question
A company has a web application hosted in an On-Demand EC2 instance. You are creating a shell script that needs the instance's public and private IP addresses.

What is the best way to get the instance's associated IP addresses which your shell script can use?

## Options
A. By using a Curl or Get Command to get the latest metadata information from http://169.254.169.254/latest/meta-data/

B. By using IAM.

C. By using a CloudWatch metric.

D. By using a Curl or Get Command to get the latest user data information from http://169.254.169.254/latest/user-data/

## Correct Answer
A

## Explanation
Instance metadata is data about your EC2 instance that you can use to configure or manage the running instance. Because your instance metadata is available from your running instance, you do not need to use the Amazon EC2 console or the AWS CLI. This can be helpful when you're writing scripts to run from your instance. For example, you can access the local IP address of your instance from instance metadata to manage a connection to an external application.

To view the private IPv4 address, public IPv4 address, and all other categories of instance metadata from within a running instance, use the following URL:

http://169.254.169.254/latest/meta-data/

Reference:

http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html

Check out this Amazon EC2 Cheat Sheet:

https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/

Tutorials Dojo's AWS Certified Solutions Architect Associate Exam Study Guide:

https://tutorialsdojo.com/aws-certified-solutions-architect-associate/


