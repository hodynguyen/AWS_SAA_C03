# Question 43

## Topic
Design Resilient Architectures

## Question
A major TV network has a web application running on eight Amazon T3 EC2 instances behind an application load balancer. The number of requests that the application processes are consistent and do not experience spikes. A Solutions Architect must configure an Auto Scaling group for the instances to ensure that the application is running at all times.

Which of the following options can satisfy the given requirements?

## Options
A. Deploy four EC2 instances with Auto Scaling in one Availability Zone and four in another availability zone in the same region behind an Amazon Elastic Load Balancer.

B. Deploy two EC2 instances with Auto Scaling in four regions behind an Amazon Elastic Load Balancer.

C. Deploy four EC2 instances with Auto Scaling in one region and four in another region behind an Amazon Elastic Load Balancer.

D. Deploy eight EC2 instances with Auto Scaling in one Availability Zone behind an Amazon Elastic Load Balancer.

## Correct Answer
A

## Explanation
The best option is to deploy four EC2 instances in one Availability Zone and four in another availability zone in the same region behind an Amazon Elastic Load Balancer. This way, if one availability zone goes down, there is still another available zone that can accommodate traffic.

Auto Scaling will launch additional EC2 instances to the remaining Availability Zone(s) in the event of an AZ outage.

**Why other options are incorrect:**
- **Option B** and **Option C** are incorrect because ELB is designed to run in one region only, not across multiple regions.
- **Option D** is incorrect because this architecture is not highly available; if that AZ goes down, the application is unreachable.

## References
- https://aws.amazon.com/elasticloadbalancing/
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-increase-availability.html
- https://tutorialsdojo.com/aws-elastic-load-balancing-elb/
