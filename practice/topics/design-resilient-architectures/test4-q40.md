# Question 40

## Topic
Design Resilient Architectures

## Question
A newly hired Solutions Architect is checking all of the security groups and network access control list rules of the company's AWS resources. For security purposes, the MS SQL connection via port 1433 of the database tier should be secured. Below is the security group configuration of their Microsoft SQL Server database:

The application tier hosted in an Auto Scaling group of EC2 instances is the only identified resource that needs to connect to the database. The Architect should ensure that the architecture complies with the best practice of granting least privilege.

Which of the following changes should be made to the security group configuration?

## Options
A. For the MS SQL rule, change the Source to the EC2 instance IDs of the underlying instances of the Auto Scaling group.

B. For the MS SQL rule, change the Source to the Network ACL ID attached to the application tier.

C. For the MS SQL rule, change the Source to the static AnyCast IP address attached to the application tier.

D. For the MS SQL rule, change the Source to the security group ID attached to the application tier.

## Correct Answer
D

## Explanation
A security group acts as a virtual firewall for your instance to control inbound and outbound traffic. When you launch an instance in a VPC, you can assign up to five security groups to the instance. Security groups act at the instance level, not the subnet level. Therefore, each instance in a subnet in your VPC can be assigned to a different set of security groups.

If you launch an instance using the Amazon EC2 API or a command line tool and you don't specify a security group, the instance is automatically assigned to the default security group for the VPC. If you launch an instance using the Amazon EC2 console, you have an option to create a new security group for the instance.

For each security group, you add rules that control the inbound traffic to instances and a separate set of rules that control the outbound traffic. This section describes the basic things that you need to know about security groups for your VPC and their rules.

Amazon security groups and network ACLs don't filter traffic to or from link-local addresses (169.254.0.0/16) or AWS reserved IPv4 addresses (these are the first four IPv4 addresses of the subnet, including the Amazon DNS server address for the VPC). Similarly, flow logs do not capture IP traffic to or from these addresses.

In the scenario, the security group configuration allows any server (0.0.0.0/0) from anywhere to establish an MS SQL connection to the database via the 1433 port. The most suitable solution here is to change the Source field to the security group ID attached to the application tier.

Hence, the correct answer is the option that says: For the MS SQL rule, change the Source to the security group ID attached to the application tier.

References:

https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html

https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Security.html

**Why other options are incorrect:**

- The option that says: For the MS SQL rule, change the Source to the EC2 instance IDs of the underlying instances of the Auto Scaling group is incorrect because using the EC2 instance IDs of the underlying instances of the Auto Scaling group as the source can cause intermittent issues. New instances will be added, and old instances will be removed from the Auto Scaling group over time, which means that you have to manually update the security group setting once again. A better solution is to use the security group ID of the Auto Scaling group of EC2 instances.

- The option that says: For the MS SQL rule, change the Source to the static AnyCast IP address attached to the application tier is incorrect because a static AnyCast IP address is primarily used for AWS Global Accelerator and not for security group configurations.

- The option that says: For the MS SQL rule, change the Source to the Network ACL ID attached to the application tier is incorrect because you have to use the security group ID instead of the Network ACL ID of the application tier. Take note that the Network ACL covers the entire subnet which means that other applications that use the same subnet will also be affected.

