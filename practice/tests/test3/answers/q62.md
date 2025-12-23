# Question 62

## Topic
Design Cost-Optimized Architectures

## Question
A solutions architect is managing an application that runs on a Windows EC2 instance with an attached Amazon FSx for Windows File Server. To save cost, management has decided to stop the instance during off-hours and restart it only when needed. It has been observed that the application takes several minutes to become fully operational which impacts productivity.

How can the solutions architect speed up the instance’s loading time without driving the cost up?

## Options
A. Migrate the application to a Linux-based EC2 instance.

B. Enable the hibernation mode on the EC2 instance.

C. Migrate the application to an EC2 instance with hibernation enabled.

D. Disable the Instance Metadata Service to reduce the things that need to be loaded at startup.

## Correct Answer
C

## Explanation
Hibernation provides the convenience of pausing and resuming the instances, saves time by reducing the startup time taken by applications, and saves effort in setting up the environment or applications all over again. Instead of having to rebuild the memory footprint, hibernation allows applications to pick up exactly where they left off.
While the instance is in hibernation, you pay only for the EBS volumes and Elastic IP Addresses attached to it; there are no other hourly charges (just like any other stopped instance).

Therefore, the correct answer is: Migrate the application to an EC2 instance with hibernation enabled.

The option that says: Migrate the application to a Linux-based EC2 instance is incorrect. This does not guarantee a faster load time. Moreover, it is a risky thing to do as the application might have dependencies tied to the previous operating system that won't work on a different OS.

The option that says: Enable the hibernation mode on the EC2 instance is incorrect. It is not possible to enable or disable hibernation for an instance after it has been launched.

The option that says: Disable the instance metadata service to reduce the things that need to be loaded at startup is incorrect. This won't affect the startup load time at all. The Instance Metadata Service is just a service that you can access over the network from within an EC2 instance.

## References
- https://aws.amazon.com/about-aws/whats-new/2019/10/amazon-ec2-hibernation-now-available-on-windows/
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/enabling-hibernation.html
- https://aws.amazon.com/blogs/aws/new-hibernate-your-ec2-instances/
- https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/
