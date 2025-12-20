# Question 35

## Topic
Design Resilient Architectures

## Question
A tech company is currently using Auto Scaling for their web application. A new AMI now needs to be used for launching a fleet of EC2 instances.

Which of the following changes needs to be done?

## Options
A. Create a new target group and launch template.

B. Create a new target group.

C. Create a new launch template.

D. Do nothing. You can start directly launching EC2 instances in the Auto Scaling group with the same launch template.

## Correct Answer
C

## Explanation
A launch template is a template that an Auto Scaling group uses to launch EC2 instances. When you create a launch template, you specify information for the instances, such as the ID of the Amazon Machine Image (AMI), the instance type, a key pair, one or more security groups, and a block device mapping.

You can't modify a launch template after you've created it. Therefore, if you want to change the launch template for an Auto Scaling group, you must create a new template and then update your Auto Scaling group with the new launch template.

**Why other options are incorrect:**
- **Option A** is incorrect because you only want to change the AMI, not the target group.
- **Option B** is incorrect because target groups are for ELB, not for changing AMIs.
- **Option D** is incorrect because you need to create a new launch template to use a new AMI.

## References
- https://docs.aws.amazon.com/autoscaling/ec2/userguide/launch-templates.html
- https://docs.aws.amazon.com/autoscaling/ec2/userguide/AutoScalingGroup.html
- https://tutorialsdojo.com/aws-auto-scaling/
