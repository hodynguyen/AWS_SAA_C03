# Question 34

## Topic
Design Cost-Optimized Architectures

## Question
The media company that you are working for has a video transcoding application running on Amazon EC2. Each EC2 instance polls a queue to find out which video should be transcoded, and then runs a transcoding process. If this process is interrupted, the video will be transcoded by another instance based on the queuing system. This application has a large backlog of videos which need to be transcoded. Your manager would like to reduce this backlog by adding more EC2 instances, however, these instances are only needed until the backlog is reduced.

In this scenario, which type of Amazon EC2 instance is the most cost-effective type to use?

## Options
A. Reserved instances

B. Spot instances

C. On-demand instances

D. Dedicated instances

## Correct Answer
B

## Explanation
You require an instance that will be used as spare compute resource to augment the transcoding process. These instances should also be terminated once the backlog has been reduced. The application can gracefully handle an unexpected termination of an EC2 instance, like in the event of a Spot instance termination.

Amazon EC2 Spot instances are spare compute capacity in the AWS cloud available at steep discounts compared to On-Demand prices (up to 90% savings).

**Why other options are incorrect:**
- **Option A** is incorrect because Reserved instances require long-term commitment and are not suitable for temporary workloads.
- **Option C** is incorrect because On-Demand is valid but more expensive than Spot.
- **Option D** is incorrect because Dedicated instances don't act as spare compute capacity.

## References
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/spot-interruptions.html
- http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/how-spot-instances-work.html
- https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/
