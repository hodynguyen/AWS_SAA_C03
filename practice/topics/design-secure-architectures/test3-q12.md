# Question 12

## Topic
Design Secure Architectures

## Question
A company has an On-Demand EC2 instance located in a subnet in AWS that hosts a web application. The security group attached to this EC2 instance has the following Inbound Rules:

The Route table attached to the VPC is shown below. You can establish an SSH connection into the EC2 instance from the Internet. However, you are not able to connect to the web server using your Chrome browser.

Which of the below steps would resolve the issue?

## Options
A. In the Route table, add this new route entry: 10.0.0.0/27 -> local

B. In the Security Group, remove the SSH rule.

C. In the Security Group, add an Inbound HTTP rule.

D. In the Route table, add this new route entry: 0.0.0.0 -> igw-b51618cc

## Correct Answer
C

## Explanation
In this particular scenario, you can already connect to the EC2 instance via SSH. This means that there is no problem in the Route Table of your VPC. To fix this issue, you simply need to update your Security Group and add an Inbound rule to allow HTTP traffic.

**Why other options are incorrect:**
- **Option A** is incorrect as there is no need to change the Route Tables since SSH already works.
- **Option B** is incorrect as doing so will not solve the issue. It will just disable SSH traffic.
- **Option D** is incorrect as there is no need to change the Route Tables.

## References
- http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_SecurityGroups.html
- https://tutorialsdojo.com/amazon-vpc/
