# Question 6

## Topic
Design Resilient Architectures

## Question
A Solutions Architect is designing a highly available environment for an application. She plans to host the application on EC2 instances within an Auto Scaling Group. One of the conditions requires data stored on root EBS volumes to be preserved if an instance terminates.

What should be done to satisfy the requirement?

## Options
A. Use AWS DataSync to replicate root volume data to Amazon S3.

B. Enable the Termination Protection option for all EC2 instances.

C. Configure ASG to suspend the health check process for each EC2 instance.

D. Set the value of DeleteOnTermination attribute of the EBS volumes to False.

## Correct Answer
D

## Explanation
By default, Amazon EBS root device volumes are automatically deleted when the instance terminates. However, by default, any additional EBS volumes that you attach at launch, or any EBS volumes that you attach to an existing instance persist even after the instance terminates. This behavior is controlled by the volume's DeleteOnTermination attribute, which you can modify.

To preserve the root volume when an instance terminates, change the DeleteOnTermination attribute for the root volume to False.

**Why other options are incorrect:**
- **Option A** is incorrect because AWS DataSync does not work with Amazon EBS volumes.
- **Option B** is incorrect because Termination Protection will just prevent your instance from being accidentally terminated, not preserve the data.
- **Option C** is incorrect because suspending the health check process will prevent the ASG from replacing unhealthy EC2 instances.

## References
- https://aws.amazon.com/premiumsupport/knowledge-center/deleteontermination-ebs/
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/terminating-instances.html
- https://tutorialsdojo.com/amazon-ebs/
