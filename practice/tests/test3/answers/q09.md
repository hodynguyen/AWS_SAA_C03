# Question 9

## Topic
Design Resilient Architectures

## Question
A FinTech startup deployed an application on an Amazon EC2 instance with attached Instance Store volumes and an Elastic IP address. The server is only accessed from 8 AM to 6 PM and can be stopped from 6 PM to 8 AM for cost efficiency using Lambda with the script that automates this based on tags.

Which of the following will occur when the EC2 instance is stopped and started? (Select TWO.)

## Options
A. The ENI (Elastic Network Interface) is detached.

B. The underlying host for the instance is possibly changed.

C. There will be no changes.

D. All data on the attached instance-store devices will be lost.

E. The Elastic IP address is disassociated with the instance.

## Correct Answers
**B. The underlying host for the instance is possibly changed.**

**D. All data on the attached instance-store devices will be lost.**

## Explanation
If you stopped an EBS-backed EC2 instance, the volume is preserved, but the data in any attached instance store volume will be erased. Keep in mind that an EC2 instance has an underlying physical host computer. If the instance is stopped, AWS usually moves the instance to a new host computer.

For EC2-VPC instances, the Elastic IP address remains associated even after stopping.

**Why other options are incorrect:**
- **Option A** is incorrect because the ENI will stay attached even if you stopped your EC2 instance.
- **Option C** is incorrect because there will be changes (host may change, instance store data will be lost).
- **Option E** is incorrect because in EC2-VPC, the EIP remains associated with your instance even after stopping it.

## References
- http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-lifecycle.html
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ComponentsAMIs.html#storage-for-the-root-device
- https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/
