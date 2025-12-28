# Question 60

## Topic
Design Resilient Architectures

## Question
A large multinational investment bank has a web application that requires a minimum of 4 EC2 instances to run to ensure that it can cater to its users across the globe. You are instructed to ensure fault tolerance of this system.

Which of the following is the best option?

## Options
A. Deploy an Auto Scaling group with 2 instances in each of 2 Availability Zones behind an Application Load Balancer.

B. Deploy an Auto Scaling group with 4 instances in one Availability Zone behind an Application Load Balancer.

C. Deploy an Auto Scaling group with 1 instance in each of 4 Availability Zones behind an Application Load Balancer.

D. Deploy an Auto Scaling group with 2 instances in each of 3 Availability Zones behind an Application Load Balancer.

## Correct Answer
D

## Explanation
Fault Tolerance is the ability of a system to remain in operation even if some of the components used to build the system fail. In AWS, this means that in the event of server fault or system failures, the number of running EC2 instances should not fall below the minimum number of instances required by the system for it to work properly. So if the application requires a minimum of 4 instances, there should be at least 4 instances running in case there is an outage in one of the Availability Zones or if there are server issues.

One of the differences between Fault Tolerance and High Availability is that the former refers to the minimum number of running instances. For example, you have a system that requires a minimum of 4 running instances and currently has 6 running instances deployed in two Availability Zones. There was a component failure in one of the Availability Zones which knocks out 3 instances. In this case, the system can still be regarded as Highly Available since there are still instances running that can accommodate the requests. However, it is not Fault-Tolerant since the required minimum of four instances has not been met.

Hence, the correct answer is: Deploy an Auto Scaling group with 2 instances in each of 3 Availability Zones behind an Application Load Balancer.

References:

https://media.amazonwebservices.com/AWS_Building_Fault_Tolerant_Applications.pdf

https://d1.awsstatic.com/whitepapers/aws-building-fault-tolerant-applications.pdf

AWS Overview Cheat Sheets:

https://tutorialsdojo.com/aws-cheat-sheets-overview/

Tutorials Dojo's AWS Certified Solutions Architect Associate Exam Study Guide:

https://tutorialsdojo.com/aws-certified-solutions-architect-associate/

**Why other options are incorrect:**

- The option that says: Deploy an Auto Scaling group with 2 instances in each of 2 Availability Zones behind an Application Load Balancer is incorrect because if one Availability Zone went out, there will only be 2 running instances available out of the required 4 minimum instances. Although the Auto Scaling group can spin up another 2 instances, the fault tolerance of the web application has already been compromised.

- The option that says: Deploy an Auto Scaling group with 4 instances in one Availability Zone behind an Application Load Balancer is incorrect because if the Availability Zone went out, there will be no running instance available to accommodate the request.

- The option that says: Deploy an Auto Scaling group with 1 instance in each of 4 Availability Zones behind an Application Load Balancer is incorrect because if one Availability Zone went out, there will only be 3 instances available to accommodate the request.

