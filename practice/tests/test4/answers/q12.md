# Question 12

## Topic
Design Secure Architectures

## Question
A company is using an On-Demand EC2 instance to host a legacy web application that uses an Amazon Instance Store-Backed AMI. The web application should be decommissioned as soon as possible and hence, you need to terminate the EC2 instance.

When the instance is terminated, what happens to the data on the root volume?

## Options
A. Data is automatically saved as an EBS snapshot.

B. Data is unavailable until the instance is restarted.

C. Data is automatically saved as an EBS volume.

D. Data is automatically deleted.

## Correct Answer
D

## Explanation
AMIs are categorized as either backed by Amazon EBS or backed by instance store. The former means that the root device for an instance launched from the AMI is an Amazon EBS volume created from an Amazon EBS snapshot. The latter means that the root device for an instance launched from the AMI is an instance store volume created from a template stored in Amazon S3.

The data on instance store volumes persist only during the life of the instance which means that if the instance is terminated, the data will be automatically deleted.

Hence, the correct answer is: Data is automatically deleted.

Reference:

https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ComponentsAMIs.html

Tutorials Dojo's AWS Certified Solutions Architect Associate Exam Study Guide:

https://tutorialsdojo.com/aws-certified-solutions-architect-associate/


