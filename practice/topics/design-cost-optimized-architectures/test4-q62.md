# Question 62

## Topic
Design Cost-Optimized Architectures

## Question
A web application requires a minimum of six Amazon Elastic Compute Cloud (EC2) instances running at all times. You are tasked to deploy the application to three availability zones in the EU Ireland region (eu-west-1a, eu-west-1b, and eu-west-1c). It is required that the system is fault-tolerant up to the loss of one Availability Zone.

Which of the following setup is the most cost-effective solution which also maintains the fault-tolerance of your system?

## Options
A. 6 instances in eu-west-1a, 6 instances in eu-west-1b, and 6 instances in eu-west-1c

B. 6 instances in eu-west-1a, 6 instances in eu-west-1b, and no instances in eu-west-1c

C. 3 instances in eu-west-1a, 3 instances in eu-west-1b, and 3 instances in eu-west-1c

D. 2 instances in eu-west-1a, 2 instances in eu-west-1b, and 2 instances in eu-west-1c

## Correct Answer
C

## Explanation
Basically, fault-tolerance is the ability of a system to remain in operation even in the event that some of its components fail without any service degradation. In AWS, it can also refer to the minimum number of running EC2 instances or resources which should be running at all times in order for the system to properly operate and serve its consumers. Take note that this is quite different from the concept of High Availability, which is just concerned with having at least one running instance or resource in case of failure.

In this scenario, 3 instances in eu-west-1a, 3 instances in eu-west-1b, and 3 instances in eu-west-1c is the correct answer because even if there was an outage in one of the Availability Zones, the system still satisfies the requirement of having a minimum of 6 running instances. It is also the most cost-effective solution among other options.

References:

https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-increase-availability.html

https://media.amazonwebservices.com/AWS_Building_Fault_Tolerant_Applications.pdf

**Why other options are incorrect:**

- The option that says: 6 instances in eu-west-1a, 6 instances in eu-west-1b, and 6 instances in eu-west-1c is incorrect. Although this solution provides the maximum fault-tolerance for the system, it entails a significant cost to maintain a total of 18 instances across 3 AZs.

- The option that says: 2 instances in eu-west-1a, 2 instances in eu-west-1b, and 2 instances in eu-west-1c is incorrect because if one Availability Zone goes down, there will only be 4 running instances available. Although this is the most cost-effective solution, it does not provide fault-tolerance.

- The option that says: 6 instances in eu-west-1a, 6 instances in eu-west-1b, and no instances in eu-west-1c is incorrect. Although it provides fault-tolerance, it is not the most cost-effective solution as compared with the options above. This solution has 12 running instances, unlike the correct answer which only has 9 instances.

