# Question 31

## Topic
Design Secure Architectures

## Question
An investment bank is working with an IT team to handle the launch of the new digital wallet system. The applications will run on multiple EBS-backed EC2 instances which will store the logs, transactions, and billing statements of the user in an S3 bucket. Due to tight security and compliance requirements, the IT team is exploring options on how to safely store sensitive data on the EBS volumes and S3.

Which of the below options should be carried out when storing sensitive data on AWS? (Select TWO.)

## Options
A. Migrate the EC2 instances from the public to private subnet.

B. Create an EBS Snapshot

C. Enable EBS Encryption

D. Use AWS Shield and WAF

E. Enable Amazon S3 Server-Side or use Client-Side Encryption

## Correct Answers
**C. Enable EBS Encryption**

**E. Enable Amazon S3 Server-Side or use Client-Side Encryption**

## Explanation
Amazon EBS encryption offers a simple encryption solution for your EBS volumes without the need to build, maintain, and secure your own key management infrastructure.

In Amazon S3, data protection refers to protecting data while in-transit and at rest. You can use Server-Side Encryption or Client-Side Encryption to protect data at rest.

**Why other options are incorrect:**
- **Option A** is incorrect because moving to private subnet is different from encrypting data.
- **Option B** is incorrect because EBS Snapshot is for backup, not security.
- **Option D** is incorrect because Shield and WAF protect against attacks, not for data encryption.

## References
- http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSEncryption.html
- http://docs.aws.amazon.com/AmazonS3/latest/dev/UsingEncryption.html
- https://tutorialsdojo.com/amazon-ebs/
