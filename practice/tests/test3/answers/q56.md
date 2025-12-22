# Question 56

## Topic
Design High-Performing Architectures

## Question
A large financial firm in the country has an AWS environment that contains several Reserved EC2 instances hosting a web application that has been decommissioned last week. To save costs, you need to stop incurring charges for the Reserved instances as soon as possible.

What cost-effective steps will you take in this circumstance? (Select TWO.)

## Options
A. Go to the Amazon.com online shopping website and sell the Reserved instances.

B. Terminate the Reserved instances as soon as possible to avoid getting billed at the on-demand price when it expires.

C. Stop the Reserved instances as soon as possible.

D. Contact AWS to cancel your AWS subscription.

E. Go to the AWS Reserved Instance Marketplace and sell the Reserved instances.

## Correct Answers
B, E

## Explanation
The Reserved Instance Marketplace is a platform that supports the sale of third-party and AWS customers' unused Standard Reserved Instances, which vary in terms of lengths and pricing options. For example, you may want to sell Reserved Instances after moving instances to a new AWS region, changing to a new instance type, ending projects before the term expiration, when your business needs change, or if you have unneeded capacity.

Hence, the correct answers are:
- Go to the AWS Reserved Instance Marketplace and sell the Reserved instances.
- Terminate the Reserved instances as soon as possible to avoid getting billed at the on-demand price when it expires.

Stopping the Reserved instances as soon as possible is incorrect because a stopped instance can still be restarted. Take note that when a Reserved Instance expires, any instances that were covered by the Reserved Instance are billed at the on-demand price which costs significantly higher. Since the application is already decommissioned, there is no point of keeping the unused instances. It is also possible that there are associated Elastic IP addresses, which will incur charges if they are associated with stopped instances

Contacting AWS to cancel your AWS subscription is incorrect as you don't need to close down your AWS account.

Going to the Amazon.com online shopping website and selling the Reserved instances is incorrect as you have to use AWS Reserved Instance Marketplace to sell your instances.

## References
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ri-market-general.html
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-lifecycle.html
- https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/
