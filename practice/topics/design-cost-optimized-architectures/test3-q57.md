# Question 57

## Topic
Design Cost-Optimized Architectures

## Question
A company is hosting EC2 instances that are on non-production environment and processing non-priority batch loads, which can be interrupted at any time.

What is the best instance purchasing option which can be applied to your EC2 instances in this case?

## Options
A. On-Demand Capacity Reservations

B. On-Demand Instances

C. Reserved Instances

D. Spot Instances

## Correct Answer
D

## Explanation
Amazon EC2 Spot instances are spare compute capacity in the AWS cloud available to you at steep discounts compared to On-Demand prices. It can be interrupted by AWS EC2 with two minutes of notification when the EC2 needs the capacity back.

To use Spot Instances, you create a Spot Instance request that includes the number of instances, the instance type, the Availability Zone, and the maximum price that you are willing to pay per instance hour. If your maximum price exceeds the current Spot price, Amazon EC2 fulfills your request immediately if capacity is available. Otherwise, Amazon EC2 waits until your request can be fulfilled or until you cancel the request.

Reserved Instances and On-Demand Capacity Reservations are better suited for workloads with steady, predictable usage, while On-Demand Instances may not be the most cost-efficient option for workloads that are flexible and non-urgent.

## References
- http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-spot-instances.html
- https://aws.amazon.com/ec2/spot/
- https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/
